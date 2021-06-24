# COVID-19 passbook Generator

The aim of this project is to let a user scan a EU Digital COVID Certificate with their smartphone, and generate a passbook, without any data stored on a remote server. Everything possible had to be done on the device itself, including especially:

- [x] Reading the QRCode & decoding it
- [x] Extracting information from it
- [x] Put the user data into the passbook template
- [x] Call the server for manifest signature
- [x] Create the passbook archive with the signature

Due to how Apple degigned their passbook, they need to be signed to be displayed in the wallet app. ~~At the moment I didn't find a way of doing this on the user's device without compromising the signing key~~ However, we just need to sign the manifest which contains `SHA-1` of your data, not the data itself. That's why we thought about a small web service, which does all of this in-memory:

- [x] [perform signature of the manifest](https://github.com/clawfire/covid19-passbook-signature)


## Contributors & open-source

[![](https://contrib.rocks/image?repo=clawfire/covid19-passbook-generator)](https://github.com/clawfire/covid19-passbook-generator/graphs/contributors)

This work could never have been done without the support of the open source community.

- [EHN DCC Schema](https://github.com/ehn-dcc-development/ehn-dcc-schema) for the JSON schema of the code content AND the list of manufacturers, tests, prophylaxis, vaccines, ...
- [Path Check DCC JS SDK](https://github.com/Path-Check/dcc-sdk.js) for the content extraction from the QR Code, since the one offered by the EHN DCC Dev team requires the pubkeys of each countries (which are undisclosed by choice)
- [Path Check debug tool](https://github.pathcheck.org/debug.html) to help explore the QR code content
- [Nimiq JS QR Scanner](https://github.com/nimiq/qr-scanner/)
- [JSZIP](https://stuk.github.io/jszip/)
