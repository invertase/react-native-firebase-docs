# Phone Auth

RNFirebase provides two methods to sign users in with their phone number; [ref auth#signInWithPhoneNumber] and [ref auth#verifyPhoneNumber]. Both provide different a different workflow to tie it best into your app; `signInWithPhoneNumber` will sign the user in automatically once the user had confirmed their phone number, whilst `verifyPhoneNumber` will provide feedback on the current verification state but requires you to manually sign the user in once confirmed.

## signInWithPhoneNumber

`signInWithPhoneNumber` is a more straight-forward implementation of handling the auth flow, however it provides less flexibility to handle the various situations which may occur. 

### Example

1. Trigger phone auth - as per the Web SDK (without the need for captcha):

```js
firebase.auth().signInWithPhoneNumber(phoneNumber)
  .then(confirmResult => // save confirm result to use with the manual verification code)
  .catch(error => /error);
```

2. Confirm verification code - as per the Web SDK:

```js
confirmResult.confirm(verificationCode)
  .then(user => // User is logged in){
  .catch(error => // Error with verification code);
```

On iOS, this is all that is required.

However Android also provides "auto verification" if Google Play service can automatically detect the incoming message (and doesn't display it!).

3. [Android] Handle Auto Verification

To handle auto verification, we need to listen to [ref auth#onAuthStateChanged]:

```js
firebase.auth().onAuthStateChanged((user) => {
  if (user) // user is verified and logged in
});
```

The below is a full implementation example:

```js
import React, { Component } from 'react';
import { View, Button, Text, TextInput, Image } from 'react-native';

import firebase from 'react-native-firebase';

const successImageUri = 'https://cdn.pixabay.com/photo/2015/06/09/16/12/icon-803718_1280.png';

export default class PhoneAuthTest extends Component {
  constructor(props) {
    super(props);
    this.unsubscribe = null;
    this.state = {
      user: null,
      message: '',
      codeInput: '',
      phoneNumber: '+44',
      confirmResult: null,
    };
  }

  componentDidMount() {
    this.unsubscribe = firebase.auth().onAuthStateChanged((user) => {
      if (user) {
        this.setState({ user: user.toJSON() });
      } else {
        // User has been signed out, reset the state
        this.setState({
          user: null,
          message: '',
          codeInput: '',
          phoneNumber: '+44',
          confirmResult: null,
        });
      }
    });
  }

  componentWillUnmount() {
     if (this.unsubscribe) this.unsubscribe();
  }

  signIn = () => {
    const { phoneNumber } = this.state;
    this.setState({ message: 'Sending code ...' });

    firebase.auth().signInWithPhoneNumber(phoneNumber)
      .then(confirmResult => this.setState({ confirmResult, message: 'Code has been sent!' }))
      .catch(error => this.setState({ message: `Sign In With Phone Number Error: ${error.message}` }));
  };

  confirmCode = () => {
    const { codeInput, confirmResult } = this.state;

    if (confirmResult && codeInput.length) {
      confirmResult.confirm(codeInput)
        .then((user) => {
          this.setState({ message: 'Code Confirmed!' });
        })
        .catch(error => this.setState({ message: `Code Confirm Error: ${error.message}` }));
    }
  };

  signOut = () => {
    firebase.auth().signOut();
  }
  
  renderPhoneNumberInput() {
   const { phoneNumber } = this.state;
      
    return (
      <View style={{ padding: 25 }}>
        <Text>Enter phone number:</Text>
        <TextInput
          autoFocus
          style={{ height: 40, marginTop: 15, marginBottom: 15 }}
          onChangeText={value => this.setState({ phoneNumber: value })}
          placeholder={'Phone number ... '}
          value={phoneNumber}
        />
        <Button title="Sign In" color="green" onPress={this.signIn} />
      </View>
    );
  }
  
  renderMessage() {
    const { message } = this.state;
  
    if (!!message.length) return null;
  
    return (
      <Text style={{ padding: 5, backgroundColor: '#000', color: '#fff' }}>{message}</Text>
    );
  }
  
  renderVerificationCodeInput() {
    const { codeInput } = this.state;
  
    return (
      <View style={{ marginTop: 25, padding: 25 }}>
        <Text>Enter verification code below:</Text>
        <TextInput
          autoFocus
          style={{ height: 40, marginTop: 15, marginBottom: 15 }}
          onChangeText={value => this.setState({ codeInput: value })}
          placeholder={'Code ... '}
          value={codeInput}
        />
        <Button title="Confirm Code" color="#841584" onPress={this.confirmCode} />
      </View>
    );
  }

  render() {
    const { user, confirmResult } = this.state;
    return (
      <View style={{ flex: 1 }}>
        
        {!user && !confirmResult && this.renderPhoneNumberInput()}
        
        {this.renderMessage()}
        
        {!user && confirmResult && this.renderVerificationCodeInput()}
        
        {user && (
          <View
            style={{
              padding: 15,
              justifyContent: 'center',
              alignItems: 'center',
              backgroundColor: '#77dd77',
              flex: 1,
            }}
          >
            <Image source={{ uri: successImageUri }} style={{ width: 100, height: 100, marginBottom: 25 }} />
            <Text style={{ fontSize: 25 }}>Signed In!</Text>
            <Text>{JSON.stringify(user)}</Text>
            <Button title="Sign Out" color="red" onPress={this.signOut} />
          </View>
        )}
      </View>
    );
  }
}
```

## verifyPhoneNumber

This implementation gives you full control of the phone number verification flow on either platform as well as a flexible api to suite any UI flow and should be familiar to use if you've used things like storage upload tasks / database on listeners.

TODO


