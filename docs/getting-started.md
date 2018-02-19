## Introduction

**React Native Firebase** makes using [Firebase](http://firebase.com) with React Native simple. It provides a _light-weight_ layer on-top of the native Firebase SDKs (iOS & Android) whilst mirroring the Firebase Web SDKs API as closely as possible.

## Why 

Although the some features from the [Firebase Web SDK](https://www.npmjs.com/package/firebase) will generally work with React Native, it is mainly built for the web and as such has a limited compatible feature set.

In contrast we use the Firebase Native SDKs - this allows us to provide APIs to a vast majority of Firebase products and services.

See the [Supported Firebase Features](#Supported-Firebase-Features) table below to compare our supported features.

---

## Getting Started

We provide several options for you to get started with React Native Firebase, select a method from the table below that matches your requirements:

|  | Manual Integration  | Basic Starter Kit | Premium Starter Kits |
|:---:|:-------------------:|:-----------------:|:--------------------:|
|  | ![manual][manual] | ![basic][basic] | ![premium][premium] |
|  | Manually integrate React Native Firebase into your project by following our Android and iOS setup guides. | We've installed React Native Firebase into the standard React Native template app with only minimal steps for you to get going.      | Don't want to start from scratch? Use one of our premium starter kits to kick start development for your next app. |
|  | Recommended for **experienced** React Native **developers** and **existing** React Native **projects**. | Recommended for **beginners** and **new** React Native **projects**. | Recommended for **beginners** and **new** React Native **projects**. |
|  | [![continue][btn-guide]](version /installation/initial-setup) | [![btn-kit][btn-kit]](http://invertase.link/get-started-basic) | [![btn-kits][btn-kits]](http://invertase.link/get-started-premium) |

---

## Supported Firebase Features
> The Web SDK column indicates what modules/functionality from the Web SDK are usable within React Native.


> '**?**' indicates partial support

| Firebase Features      | v1.x.x  | v2.x.x  | v3.x.x | v3.1.x | v3.2.x | Web SDK |
| ---------------------- | :---: | :---: | :---: | :---: | :---: | :---: |
| **AdMob**                  | ❌ | ✅ | ✅ | ✅ | ✅ | ❌ |
| **Analytics**              | ✅ | ✅ | ✅ | ✅ | ✅ | ❌ |
| **App Indexing**           | ❌ | ❌ | ❌ | ❌ | ❌ | ❌ |
| **Authentication**         | ✅ | ✅ | ✅ | ✅ | ✅ | ✅ |
| _-- Phone Auth_            | ❌ | ❌ | ✅ | ✅ | ✅ | ❌ |
| **Core**                   | ❌ |**?**| ✅ | ✅ | ✅ | ✅ |
|  _-- Multiple Apps_        | ❌ | ❌ | ✅ | ✅ | ✅ | ✅ |
| **Cloud Firestore**        | ❌ | ❌ | ✅ | ✅ | ✅ |**?**|
| **Cloud Messaging (FCM)**  | ✅ | ✅ | ✅ | ✅ | ✅ |**?**|
| **Crashlytics**            | ❌ | ❌ | ❌ | ❌ | ✅ | ❌ |
| **Crash Reporting**        | ✅ | ✅ | ✅ | ✅ | ✅ | ❌ |
| **Dynamic Links**          | ❌ | ❌ | ❌ | ✅ | ✅ | ❌ |
| **Invites**                | ❌ | ❌ | ❌ |**?**|**?**| ❌ |
| **Performance Monitoring** | ✅ | ✅ | ✅ | ✅ | ✅ | ❌ |
| **Realtime Database**      | ✅ | ✅ | ✅ | ✅ | ✅ | ✅ |
| _-- Offline Persistence_   | ✅ | ✅ | ✅ | ✅ | ✅ |**?**|
| _-- Transactions_          | ✅ | ✅ | ✅ | ✅ | ✅ | ✅ |
| **Remote Config**          | ✅ | ✅ | ✅ | ✅ | ✅ | ❌ |
| **Storage**                | ✅ | ✅ | ✅ | ✅ | ✅ |**?**|

---

### Supported versions - React Native / Firebase

> The table below shows the supported versions of React Native and the Firebase SDKs for different versions of `react-native-firebase`

|                        | 1.X.X       | 2.0.X       | 2.1.X / 2.2.X   | 3.0.X    |  3.1.X      |  3.2.X   |
|------------------------|-------------|-------------|-----------------|----------|-------------|----------|
| React Native           | 0.36 - 0.39 | 0.40 - 0.46 | 0.47 +          | 0.48 +   | 0.48 - 0.49 | 0.50 +   |
| Firebase Android SDK   | 10.2.0 +    | 11.0.0 +    | 11.0.0 +        | 11.4.2 + | 11.6.0 +    | 11.6.2 + |
| Firebase iOS SDK       | 3.15.0 +    | 4.0.0 +     | 4.0.0 +         | 4.3.0 +  | 4.5.0 +     | 4.7.0 +  |

---

## Questions

For questions and support please use our [Discord chat](https://discord.gg/C9aK28N) or [Stack Overflow](https://stackoverflow.com/questions/tagged/react-native-firebase). The issue list of this repo is **exclusively** for bug reports.

## Issues

Please make sure to complete the issue template before opening an issue. Issues not conforming to the guidelines may be closed immediately.

## Feature Requests

For feature requests please use our [Canny Board](http://invertase.link/requests).

## Changelog

Detailed changes for each release are documented in the [releases notes](https://github.com/invertase/react-native-firebase/releases).

<hr>

## Supporting React Native Firebase

React Native Firebase is an Apache-2.0 licensed open source project. It's an independent project with its ongoing development made possible entirely thanks to the support by these awesome [sponsors](#sponsors) and [backers](#backers). If you'd like to join them, please consider:

- [Become a backer or sponsor on Open Collective](https://opencollective.com/react-native-firebase).

### Sponsors

Support this project by becoming a sponsor. Your logo will show up here with a link to your website. [[Become a sponsor](https://opencollective.com/react-native-firebase#sponsor)]

<a href="https://opencollective.com/react-native-firebase/sponsor/0/website" target="_blank"><img src="https://opencollective.com/react-native-firebase/sponsor/0/avatar.svg"></a><a href="https://opencollective.com/react-native-firebase/sponsor/1/website" target="_blank"><img src="https://opencollective.com/react-native-firebase/sponsor/1/avatar.svg"></a><a href="https://opencollective.com/react-native-firebase/sponsor/2/website" target="_blank"><img src="https://opencollective.com/react-native-firebase/sponsor/2/avatar.svg"></a><a href="https://opencollective.com/react-native-firebase/sponsor/3/website" target="_blank"><img src="https://opencollective.com/react-native-firebase/sponsor/3/avatar.svg"></a><a href="https://opencollective.com/react-native-firebase/sponsor/4/website" target="_blank"><img src="https://opencollective.com/react-native-firebase/sponsor/4/avatar.svg"></a><a href="https://opencollective.com/react-native-firebase/sponsor/5/website" target="_blank"><img src="https://opencollective.com/react-native-firebase/sponsor/5/avatar.svg"></a><a href="https://opencollective.com/react-native-firebase/sponsor/6/website" target="_blank"><img src="https://opencollective.com/react-native-firebase/sponsor/6/avatar.svg"></a><a href="https://opencollective.com/react-native-firebase/sponsor/7/website" target="_blank"><img src="https://opencollective.com/react-native-firebase/sponsor/7/avatar.svg"></a><a href="https://opencollective.com/react-native-firebase/sponsor/8/website" target="_blank"><img src="https://opencollective.com/react-native-firebase/sponsor/8/avatar.svg"></a><a href="https://opencollective.com/react-native-firebase/sponsor/9/website" target="_blank"><img src="https://opencollective.com/react-native-firebase/sponsor/9/avatar.svg"></a>

### Backers

Thank you to all our backers! 🙏 [[Become a backer](https://opencollective.com/react-native-firebase#backer)]

<a href="https://opencollective.com/react-native-firebase#backers" target="_blank"><img src="https://opencollective.com/react-native-firebase/backers.svg?width=890"></a>

### Contributing

Please make sure to read the [Contributing Guide](https://github.com/invertase/react-native-firebase/blob/master/CONTRIBUTING.md) before making a pull request.

Thank you to all the people who have already contributed to React Native Firebase!

<a href="graphs/contributors"><img src="https://opencollective.com/react-native-firebase/contributors.svg?width=890" /></a>

<hr>

[manual]: https://rnfirebase.io/static/media/docs-vector.cb67f7d6.png "Recommended for experienced React Native developers and existing React Native projects."
[basic]: https://rnfirebase.io/static/media/starter-project-vector.e45d010a.png "Recommended for beginners and new React Native projects."
[premium]: https://rnfirebase.io/static/media/premium-kits-vector.dc0245df.png "Recommended for beginners and new React Native projects."
[btn-guide]: https://i.imgur.com/Tmp5hku.png "View the integration guide"
[btn-kit]: https://i.imgur.com/N7GUGXo.png "Go to the basic starter kit repo"
[btn-kits]: https://i.imgur.com/1rmzlpV.png "Go to the basic starter kit repo"