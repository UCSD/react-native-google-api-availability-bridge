# React Native Google API Availability Bridge
Check if user has google play services installed + updated from React Native, Android only
<https://developers.google.com/android/reference/com/google/android/gms/common/GoogleApiAvailability.html>

## Installation
```
npm install --save react-native-google-api-availability-bridge
react-native link
```

Requires >= 0.32 RN

## Usage
```js
const GoogleAPIAvailability = require('react-native-google-api-availability-bridge');

GoogleAPIAvailability.checkGooglePlayServices((result) => {
	if(result === 'update') {
		GoogleAPIAvailability.promptGooglePlayUpdate(false);
	}
});
```

```js
<View>
	<Text>Please update Google Play Services to view map</Text>
	<TouchableHighlight onPress={() => GoogleAPIAvailability.openGooglePlayUpdate()}>
		<Text>Update</Text>
	</TouchableHighlight>
</View>
```

### Methods

| Method Name | Arguments | Notes
|---|---|---|
|`checkGooglePlayServices`|`result`|-Returns a promise with the Play Services status. `success` everything is good, `failure` if something goes wrong, `update` if services are not on the latest version, `missing` if services are missing, `invalid` if they are not setup correctly, `disabled` if services are disabled. |
|`promptGooglePlayUpdate`|`allowUse`|-Brings a popup window prompting user to update their Play Services. -Accepts a boolean that can force quit the application if the user does not wish to update|
|`openGooglePlayUpdate`|*none*|-Opens Google Play Services in the Play Store application|

## TODO

* Add Example App
* Expose more API functions
