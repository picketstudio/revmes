## 30/01/2020 Notes

- In it's original incarnation, the versioning scheme captured the whether a native or codepush was made, as well as the nature of the change (namely a feature or bugfix)
- This is limited in the sense that if a new feature or bugfix in `js` is created, it can only be deployed to the latest version of the native app.
	- This is because every native change will increment the `MAJOR` number
- Instead, the question we really want to know is:
	- given any change to the `js` (major, minor, patch), what is the oldest version of the app which is **100% guaranteed** safe so that the `js bundle` that is downloaded from `CodePush` is executed within the native app.
	- this naturally leads to how to define what is *safe* in the context of deployments?
		- the idea of *safety* means that a given `js bundle` can be deployed to a particular version of the native app that is live on users devices, without crashing.
		- When would the app crash?
			- when the `js` tries to call a function/method from a `native module` that does not exist
	- to capture *safety* in the version scheme, the rules are:
		- a native change that **increases** the API surface area for `js` increments the first number (e.g. adding a react-native native module, `react-native-location` for example)
		- a native change that **removes** from or **patches** the existing API surface area for `js` increments the second number
		- a codepush deployment of the `js` will incremement the last number
	- scheme roughly is: `JS_API_INCREASE`.`JS_API_SAME_OR_LESS`.`JS_CODEPUSH_DEPLOYMENT`
- Still need to convince ourselves that this convers all possible cases
	- TODO: case analysis
