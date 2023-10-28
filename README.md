# homebridge-appletv-enhanced

[![mit license](https://badgen.net/badge/license/MIT/red)](https://github.com/maxileith/homebridge-appletv-enhanced/blob/master/LICENSE)
[![npm](https://img.shields.io/npm/v/homebridge-appletv-enhanced)](https://www.npmjs.com/package/homebridge-appletv-enhanced)
[![npm](https://badgen.net/npm/dt/homebridge-appletv-enhanced)](https://www.npmjs.com/package/homebridge-appletv-enhanced)
[![donate](https://badgen.net/badge/donate/paypal/91BE09)](https://www.paypal.me/maxileith)

[Homebridge](https://github.com/homebridge/homebridge) plugin that exposes the Apple TV to HomeKit with much richer features than the vanilla Apple TV integration of HomeKit.

This plugin automatically discovers Apple TV devices in the local network and exposes each one as a HomeKit Set-Top Box.

## Features

-   Automatically discover Apple TVs in your local network.
-   Pairing process without the need to access the command line like with other plugins.
-   Change the current App by selecting an input in HomeKit.
    -   The plugin is developed in a way that makes it possible to rename, hide or show inputs in HomeKit natively ... and safes it.
-   For each media type (music, video, tv and unknown) the plugin will create a motion sensor (media types can be hidden or shown by changing the configuration).
-   For each device state (idle, playing, loading, seeking, paused, stopped) the plugin will create a motion sensor (device states can be hidden or shown by changing the configuration).
-   If you do not want all Apple TVs to be exposed, it is possible to blacklist them by providing the MAC-Address.

## Pairing

After installing and starting the plugin devices will automatically be discovered. Look out for warning messages (yellow) in the log. You will be asked to pair your Apple TV. In order to do that, just the link displayed in the log message, e.g. http://192.168.0.16:42015/. On this page you can enter the 4-digit PIN displayed on your Apple TV to pair it.

<img src="https://raw.githubusercontent.com/maxileith/homebridge-appletv-enhanced/main/docs/img/enterPIN.jpg" width=280/> <img src="https://raw.githubusercontent.com/maxileith/homebridge-appletv-enhanced/main/docs/img/pinTransmitted.jpg" width=280/>

After you have entered the PIN, you need to check the logs if pairing was successful. If you entered a wrong PIN or the pairing request expired, a new attempt will be initiated. Take a look into the logs, there you will find the link to the new pairing page.

If you enter the PIN wrong or let the pairing request timeout too often, you will need to wait to start a new pairing attempt.

## Capabilities

The screenshots speak for themselves ...

<img src="https://raw.githubusercontent.com/maxileith/homebridge-appletv-enhanced/main/docs/img/inputs.png" width=280/> <img src="https://raw.githubusercontent.com/maxileith/homebridge-appletv-enhanced/main/docs/img/sensors.png" width=280/>

## Important information from behind the scenes

## Configuration

This easiest way to use this plugin is to use [homebridge-config-ui-x](https://www.npmjs.com/package/homebridge-config-ui-x).  
To configure manually, add the following to the `platforms` section of Homebridge's `config.json` after installing the plugin.

**Config:**

```json
{
    "name": "Apple TV Enhanced",
    "platform": "AppleTVEnhanced",
    "mediaTypes": ["music", "video", "tv", "unknown"],
    "deviceStates": [
        "idle",
        "playing",
        "loading",
        "seeking",
        "paused",
        "stopped"
    ],
    "blacklist": ["AA:BB:CC:DD:EE:FF"]
}
```
