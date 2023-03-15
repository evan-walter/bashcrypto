# bashcrypto

## Update

After I upgraded from MacOS Monterey to Ventura, I was unable to run this script. I started a fix per [this post](https://community.jamf.com/t5/jamf-pro/encrypted-openssl-aes-256-macos-monterey-cannot-be-decrypted-with/td-p/277416). I have not finished implementing the fix. As a solution for now, I was able to successfully execute the following command on my local machine using the encryption password I had created.

`openssl aes-256-cbc -d -a -md md5 -in INPUT -out OUTPUT`
## Usage

### Options
```bash
Usage: bashcrypt [OPTION] -i INPUT -o OUTPUT
-p	use public/privatekey for encryption/decryption
-e	encrypt
-d	decrypt
-i	input
-o	output
-s	create shasum
-t  tarmode
-h	help message
```
### Create public/private key
```bash
# Create public/private key
openssl req -x509 -nodes -newkey rsa:4096 -keyout privatekey.pem -out publickey.pem
# Create public/private key with password protection
openssl req -x509 -newkey rsa:4096 -keyout privatekey.pem -out publickey.pem
```
### Encrypt
```bash
# encrypt with a password:
./bashcrypto -e -i test.txt -o test.txt.enc
# encrypt all files in a folder
./bashcrypto -e -i dir -o enc
# encrypt with your public key:
./bashcrypto -e -p public.pem -i test.txt -o ultrasecret.dat
# encrypt all files in a folder
./bashcrypto -e -p public.pem -i dir -o ultrasecret.dat
```
### Decrypt
```bash
# decrypt with password:
./bashcrypto -d -i test.txt.enc -o plain.txt
# decrypt with private key:
./bashcrypto -d -p private.pem -i ultrasecret.dat -o plain.txt
```

## To-Do
- ?
