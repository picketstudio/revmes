# Revmes Versioning 1.0.3

## Why Use Revmes Versioning?

When developing and deploying mobile applications with [React Native](https://reactnative.dev/), you have the ability to push application updates via two mechanisms:

#### App Stores

When submitting an application update to an App Store, the application native code is re-compiled and the JavaScript rebundled. The user downloads the 100% new application code onto their device.

#### Over-The-Air (OTA).

When udating via OTA only the JavaScript is rebundled. It is then sent to the user who downloads and updates their current application instance.

### The Problem revmes tries to address

When updating your application via OTA you inevitably run into the issue of how to support as many possible versions of the application in the wild safely. *Safety* in this case means that a given `JavaScript bundle` is **100% guaranteed** be deployed to a particular version of the native app that is live on users devices, without crashing.

What happens when you update your application's JavaScript bundle, push a new update via OTA but it breaks on devices that are using older versions of your application because the new JavaScript changes you just pushed relied on a native module that didn't exist in older versions of your application?

## Scheme

Given a version number MAJOR.MINOR.PATCH, increment the:

1. `MAJOR` version when a native model change increases the exposed JavaScript API surface area
2. `MINOR` version when a native model change decreases or changes the exposed JavaScript API surface area
3. `PATCH` version when a change to the JavaScript API is sent via OTA

There are NO additional labels for pre-release and build metadata available as extensions to the MAJOR.MINOR.PATCH format.

# Examples

Say we have a mobile application that needs to be released to a mobile application shopfront (App Store, Google Play Store). It will receive further updates.

1. An initial version of the app MyBeautifulApp is released: `1.0.0`
2. A native module, [@react-native-community/voice](https://github.com/react-native-community/voice), is added, increasing the JavaScript API surface area: `2.0.0`
3. A native module is removed, [@react-native-community/audio-toolkit](https://github.com/react-native-community/react-native-audio-toolkit), decreasing the JavaScript API surface area: `2.1.0`
4. A bug fix to the JavaScript API is added via OTA: `2.1.1`
4. A feature to the JavaScript API is added via OTA: `2.1.2`
5. An update to a native module, [@react-native-community/voice](https://github.com/react-native-community/voice), increasing the JavaScript API surface area: `3.0.0`

## Backus-Naur From Grammar for Revmes Versioning

	<version core> ::= <major> "." <minor> "." <patch>

	<major> ::= <numeric identifier>
	<minor> ::= <numeric identifier>
	<patch> ::= <numeric identifier>

	<numeric identifier> ::= "0"
							| <positive digit>
							| <positive digit> <digits>

	<digit> ::= "0"
				| <positive digit>

	<positive digit> ::= "1" | "2" | "3" | "4" | "5" | "6" | "7" | "8" | "9"

## FAQ

I'm sure they'll be lots...

**What's with the name?**

Think about it...

## About

The Revmes Versioning specification is authored by [Cameron Bourke](https://github.com/cameronbourke) and [Vito Belgiorno-Zegna](https://github.com/vitalbone).

If you'd like to leave feedback, please [open an issue on GitHub](https://github.com/picketstudio/revmes/issues).

## License

[Creative Commons - CC 4.0](https://creativecommons.org/licenses/by/4.0)
