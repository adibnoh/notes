# Facebook

## Facebook login integration

### Generate Hash Key

There are 3 hash key you need to generate

#### 1st is debug hash key

Run this command:

`keytool -exportcert -alias androiddebugkey -keystore ~/.android/debug.keystore | openssl sha1 -binary | openssl base64`

if asked for password, type `android`

Hash key should be generated now.

#### 2nd is release hash key

Run this command:

`keytool -exportcert -alias <release_key_alias> -keystore <release_key_path> | openssl sha1 -binary | openssl base64`

if asked for password, type your release key password

Hash key should be generated now.

#### 3rd is app signing hash key

1. Go to Google Play Console
2. Navigate to `Release Management` > `App Signing`
3. Copy SHA-1 App Signing Certificate fingerprint, remove `SHA1: `
4. Paste certificate to this website [http://tomeko.net/online_tools/hex_to_base64.php](http://tomeko.net/online_tools/hex_to_base64.php)
5. Convert to base64.
6. Hash key should be generated now.

#### Apply Hash Key to Facebook Developer Page

1. Go to Facebook Developer page.
2. Select your Choosen App
3. Navigate to `Settings` > `Basic`
4. Move to Android Section
5. Paste new generated certificate into Key Hashes field