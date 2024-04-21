
# react-native-google-play-integrity

## Getting started

`$ npm install @erickcrus/react-native-google-play-integrity --save`

### Mostly automatic installation

`$ react-native link @erickcrus/react-native-google-play-integrity`

### Manual installation


#### Android

1. Open up `android/app/src/main/java/[...]/MainActivity.java`
  - Add `import sk.kedros.playintegrity.RNGooglePlayIntegrityPackage;` to the imports at the top of the file
  - Add `new RNGooglePlayIntegrityPackage()` to the list returned by the `getPackages()` method
2. Append the following lines to `android/settings.gradle`:
  	```
  	include ':@erickcrus/react-native-google-play-integrity'
  	project(':@erickcrus/react-native-google-play-integrity').projectDir = new File(rootProject.projectDir, 	'../node_modules/@erickcrus/react-native-google-play-integrity/android')
  	```
3. Insert the following lines inside the dependencies block in `android/app/build.gradle`:
  	```
    implementation project(':@erickcrus/react-native-google-play-integrity')
  	```


## Usage
```javascript
import PlayIntegrity from '@erickcrus/react-native-google-play-integrity';

// Checks if Google Play Integrity API is available
const isAvailable = await PlayIntegrity.isPlayIntegrityAvailable();

// Request integrity token
try {
	const nonce = ... // Randomly generated nonce
	const integrityToken = await PlayIntegrity.requestIntegrityToken(nonce);
} catch (e) {
	// e.code 	- IntegrityErrorCode, see https://developer.android.com/google/play/integrity/reference/com/google/android/play/core/integrity/model/IntegrityErrorCode.html#summary
	// e.message 	- Error message
}
```
