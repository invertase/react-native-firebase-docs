# Sizes

Sets the size of an Advert. Can be one of the following or a custom size:

| Size              | Description                                                                                            |
| ----------------- | ------------------------------------------------------------------------------------------------------ |
| BANNER            | Mobile Marketing Association (MMA) banner ad size (320x50 density-independent pixels).                 |
| FULL_BANNER       | Interactive Advertising Bureau (IAB) full banner ad size (468x60 density-independent pixels).          |
| LARGE_BANNER      | Large banner ad size (320x100 density-independent pixels).                                             |
| LEADERBOARD       | Interactive Advertising Bureau (IAB) leaderboard ad size (728x90 density-independent pixels).          |
| MEDIUM_RECTANGLE  | Interactive Advertising Bureau (IAB) medium rectangle ad size (300x250 density-independent pixels).    |
| SMART_BANNER      | A dynamically sized banner that is full-width and auto-height.                                         |

To specify a custom size, pass a string with the width and height split by an "x" (follows the Regex pattern `([0-9]+)x([0-9]+)`), e.g 320x150

!> Requesting an advert with a size which does not exist on the AdMob servers will return `admob/error-code-internal-error`.
