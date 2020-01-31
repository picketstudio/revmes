# Revmes Versioning 1.0.1

# What's the problem we're trying to solve?

When developing and deploying mobile applications that have the ability to send Over The Air (OTA) updates you inevitably run into the issue of how to support as many possible versions of the application in the wild safely. *Safety* in this case means that a given `JS bundle` is **100% guaranteed** be deployed to a particular version of the native app that is live on users devices, without crashing.

## Scheme

Given a version number MAJOR.MINOR.PATCH, increment the:

1. `MAJOR` version when a native model change increases the exposed JS API surface area
2. `MINOR` version when a native model change decreases or changes the exposed JS API surface area
3. `PATCH` version when a change to the JS API is sent via OTA

There are NO additional labels for pre-release and build metadata available as extensions to the MAJOR.MINOR.PATCH format.

# Examples

Say we have a mobile application that needs to be released to an mobile application shopfront. It will receive further updates.

1. An initial version is released: `1.0.0`
2. A native module is added, increasing the JS API surface area: `2.0.0`
3. A native module is removed, decreasing the JS API surface area: `2.1.0`
4. A bug fix to the JS API is added via OTA: `2.1.1`
4. A feature to the JS API is added via OTA: `2.1.2`
5. An update to a native module, increasing the JS API surface area: `3.0.0`

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

If you'd like to leave feedback, please open an issue on GitHub.

## License

[Creative Commons - CC 4.0](https://creativecommons.org/licenses/by/4.0)
