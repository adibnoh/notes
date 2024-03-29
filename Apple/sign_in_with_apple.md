# Sign in with Apple

[What the Heck is Sign In with Apple?](https://developer.okta.com/blog/2019/06/04/what-the-heck-is-sign-in-with-apple)

## Go to Apple Developer Portal https://developer.apple.com/

### Create App ID

Set Bundler ID - follow apple convention reverse dns styling. For com.example

Enabled Sign in with Apple capabilities.

### Create Service ID

Ensure Sign in with Apple is enabled and configured

#### Sign in with Apple Configuration

Choose Primary App ID

Configure Website URLs - Apple doesn't support localhost

After finish, you will get `client_id`. Store `client_id` for later use.

### Private Key

In Apple Developer dashboard page, go to `Keys`.

Enable Sign in with Apple

Configure Sign in with Apple

After finish, download key and save it safely, you won't be able to redownload this key anymore. Also store `key_id` for later use.

## Generate Client Secret

We're using Ruby scripts to generate client secret.

Install JWT - `gem install jwt`

Create `client_secret.rb` or any name you preferred.

```rb

require 'jwt'

key_file = 'key.txt'
team_id = ''
client_id = ''
key_id = ''

ecdsa_key = OpenSSL::PKey::EC.new IO.read key_file

headers = {
  'kid' => key_id
}

claims = {
	'iss' => team_id,
	'iat' => Time.now.to_i,
	'exp' => Time.now.to_i + 86400*180,
	'aud' => 'https://appleid.apple.com',
	'sub' => client_id,
}

token = JWT.encode claims, ecdsa_key, 'ES256', headers

puts token

```

Execute `client_secret.db` - `ruby client_secret.rb`

## Integrate with Laravel

https://socialiteproviders.com/Apple/#installation-basic-usage

https://bannister.me/blog/generating-a-client-secret-for-sign-in-with-apple-on-each-request

## Sending email to private Apple email

When user sign in to your site using Sign In With Apple. They may choose to hide their email using private Apple email.

This private Apple email will blocked all unauthorized sender.

To allow our transactional mail service (such as Mailgun) to send email to our users, we need to add our domain, subdomain and email address into "Sign in with Apple for Email Communication".

Sign in to Apple Developer page, [https://developer.apple.com](https://developer.apple.com). 

Go to Services, [https://developer.apple.com/account/resources/services/list](https://developer.apple.com/account/resources/services/list).

In the section "Sign in with Apple for Email Communication", click configure button.

Inside Configuration page, add domain, subdomain and email address in Email Sources section.

Reference:

[https://medium.com/@nmpyt21/mandrill-send-to-apple-private-email-e7514f74d8be](Mandrill Send to Apple Private Email)