# Faker

Generate massive amounts of fake data in the browser and node.js.

[![Chat on Discord](https://img.shields.io/discord/929487054990110771)](https://discord.com/invite/4qDjAmDj4P)

## FAQ - What happened to the original faker.js?

This project was originally created and hosted at https://github.com/marak/Faker.js/ - however around 4th Jan, 2022 - the author decided to delete the repository (for unknown reasons).

In the interest of the community, it has been decided that faker.js will continue to be maintained here and all help in its development will be appreciated.

## Demo

Coming soon!

## Usage

### Browser

```html
<script src="faker.js" type="text/javascript"></script>
<script>
  var randomName = faker.name.findName(); // Caitlyn Kerluke
  var randomEmail = faker.internet.email(); // Rusty@arne.info
  var randomCard = faker.helpers.createCard(); // random contact card containing many properties
</script>
```

### Node.js

```js
var faker = require('faker');
var randomName = faker.name.findName(); // Rowan Nikolaus
var randomEmail = faker.internet.email(); // Kassandra.Haley@erich.biz
var randomCard = faker.helpers.createCard(); // random contact card containing many properties
```

## API

### JSDoc API Browser

[http://marak.github.io/faker.js/](http://marak.github.io/faker.js/)

### API Methods

- address
  - zipCode
  - zipCodeByState
  - city
  - cityPrefix
  - citySuffix
  - cityName
  - streetName
  - streetAddress
  - streetSuffix
  - streetPrefix
  - secondaryAddress
  - county
  - country
  - countryCode
  - state
  - stateAbbr
  - latitude
  - longitude
  - direction
  - cardinalDirection
  - ordinalDirection
  - nearbyGPSCoordinate
  - timeZone
- animal
  - dog
  - cat
  - snake
  - bear
  - lion
  - cetacean
  - horse
  - bird
  - cow
  - fish
  - crocodilia
  - insect
  - rabbit
  - type
- commerce
  - color
  - department
  - productName
  - price
  - productAdjective
  - productMaterial
  - product
  - productDescription
- company
  - suffixes
  - companyName
  - companySuffix
  - catchPhrase
  - bs
  - catchPhraseAdjective
  - catchPhraseDescriptor
  - catchPhraseNoun
  - bsAdjective
  - bsBuzz
  - bsNoun
- database
  - column
  - type
  - collation
  - engine
- datatype
  - number
  - float
  - datetime
  - string
  - uuid
  - boolean
  - hexaDecimal
  - json
  - array
- date
  - past
  - future
  - between
  - betweens
  - recent
  - soon
  - month
  - weekday
- fake
- finance
  - account
  - accountName
  - routingNumber
  - mask
  - amount
  - transactionType
  - currencyCode
  - currencyName
  - currencySymbol
  - bitcoinAddress
  - litecoinAddress
  - creditCardNumber
  - creditCardCVV
  - ethereumAddress
  - iban
  - bic
  - transactionDescription
- git
  - branch
  - commitEntry
  - commitMessage
  - commitSha
  - shortSha
- hacker
  - abbreviation
  - adjective
  - noun
  - verb
  - ingverb
  - phrase
- helpers
  - randomize
  - slugify
  - replaceSymbolWithNumber
  - replaceSymbols
  - replaceCreditCardSymbols
  - repeatString
  - regexpStyleStringParse
  - shuffle
  - mustache
  - createCard
  - contextualCard
  - userCard
  - createTransaction
- image
  - image
  - avatar
  - imageUrl
  - abstract
  - animals
  - business
  - cats
  - city
  - food
  - nightlife
  - fashion
  - people
  - nature
  - sports
  - technics
  - transport
  - dataUri
  - lorempixel
  - unsplash
  - lorempicsum
- internet
  - avatar
  - email
  - exampleEmail
  - userName
  - protocol
  - httpMethod
  - url
  - domainName
  - domainSuffix
  - domainWord
  - ip
  - ipv6
  - port
  - userAgent
  - color
  - mac
  - password
- lorem
  - word
  - words
  - sentence
  - slug
  - sentences
  - paragraph
  - paragraphs
  - text
  - lines
- mersenne
  - rand
  - seed
  - seed_array
- music
  - genre
- name
  - firstName
  - lastName
  - middleName
  - findName
  - jobTitle
  - gender
  - prefix
  - suffix
  - title
  - jobDescriptor
  - jobArea
  - jobType
- phone
  - phoneNumber
  - phoneNumberFormat
  - phoneFormats
- system
  - fileName
  - commonFileName
  - mimeType
  - commonFileType
  - commonFileExt
  - fileType
  - fileExt
  - directoryPath
  - filePath
  - semver
- time
  - recent
- unique
- vehicle
  - vehicle
  - manufacturer
  - model
  - type
  - fuel
  - vin
  - color
  - vrm
  - bicycle

### Faker.fake()

faker.js contains a super useful generator method `Faker.fake` for combining faker API methods using a mustache string format.

**Example:**

```js
console.log(
  faker.fake('{{name.lastName}}, {{name.firstName}} {{name.suffix}}')
);
```

This will interpolate the format string with the value of methods `name.lastName()`, `name.firstName()`, and `name.suffix()`

## Localization

As of version `v2.0.0` faker.js has support for multiple localities.

The default language locale is set to English.

Setting a new locale is simple:

```js
// sets locale to de
faker.locale = 'de';
```

- az
- ar
- cz
- de
- de_AT
- de_CH
- en
- en_AU
- en_AU_ocker
- en_BORK
- en_CA
- en_GB
- en_IE
- en_IND
- en_US
- en_ZA
- es
- es_MX
- fa
- fi
- fr
- fr_CA
- fr_CH
- ge
- hy
- hr
- id_ID
- it
- ja
- ko
- nb_NO
- ne
- nl
- nl_BE
- pl
- pt_BR
- pt_PT
- ro
- ru
- sk
- sv
- tr
- uk
- vi
- zh_CN
- zh_TW

### Individual Localization Packages

faker.js supports incremental loading of locales.

By default, requiring `faker` will include _all_ locale data.

In a production environment, you may only want to include the locale data for a specific set of locales.

```js
// loads only de locale
var faker = require('faker/locale/de');
```

## Setting a randomness seed

If you want consistent results, you can set your own seed:

```js
faker.seed(123);

var firstRandom = faker.datatype.number();

// Setting the seed again resets the sequence.
faker.seed(123);

var secondRandom = faker.datatype.number();

console.log(firstRandom === secondRandom);
```

## Tests

```shell
npm install .
npm run test
```

You can view a code coverage report generated in coverage/lcov-report/index.html.

## Building faker.js

faker uses [gulp](http://gulpjs.com/) to automate its build process. Each build operation is a separate task which can be run independently.

### Browser Bundle

```shell
npm run browser
```

### Building JSDocs

[JSDOC](https://jsdoc.app/) v3 HTML API documentation

```shell
npm run jsdoc
```

## Version Release Schedule

faker.js is a popular project used by many organizations and individuals in production settings. Major and Minor version releases are generally on a monthly schedule. Bugs fixes are addressed by severity and fixed as soon as possible.

If you require the absolute latest version of `faker.js` the `master` branch @ <http://github.com/marak/faker.js/> should always be up to date and working.

## Maintainer

#### Marak Squires

faker.js - Copyright (c) 2020
Marak Squires
www.marak.com
http://github.com/marak/faker.js/

faker.js was inspired by and has used data definitions from:

- <https://github.com/stympy/faker/> - Copyright (c) 2007-2010 Benjamin Curtis
- <http://search.cpan.org/~jasonk/Data-Faker-0.07/> - Copyright 2004-2005 by Jason Kohles

Permission is hereby granted, free of charge, to any person obtaining
a copy of this software and associated documentation files (the
"Software"), to deal in the Software without restriction, including
without limitation the rights to use, copy, modify, merge, publish,
distribute, sublicense, and/or sell copies of the Software, and to
permit persons to whom the Software is furnished to do so, subject to
the following conditions:

The above copyright notice and this permission notice shall be
included in all copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND,
EXPRESS OR IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF
MERCHANTABILITY, FITNESS FOR A PARTICULAR PURPOSE AND
NONINFRINGEMENT. IN NO EVENT SHALL THE AUTHORS OR COPYRIGHT HOLDERS BE
LIABLE FOR ANY CLAIM, DAMAGES OR OTHER LIABILITY, WHETHER IN AN ACTION
OF CONTRACT, TORT OR OTHERWISE, ARISING FROM, OUT OF OR IN CONNECTION
WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE SOFTWARE.

## Backers

Support us with a monthly donation and help us continue our activities. [[Become a backer](https://opencollective.com/fakerjs#backer)]

<a href="https://opencollective.com/fakerjs/backer/0/website" target="_blank"><img src="https://opencollective.com/fakerjs/backer/0/avatar.svg"></a>
<a href="https://opencollective.com/fakerjs/backer/1/website" target="_blank"><img src="https://opencollective.com/fakerjs/backer/1/avatar.svg"></a>
<a href="https://opencollective.com/fakerjs/backer/2/website" target="_blank"><img src="https://opencollective.com/fakerjs/backer/2/avatar.svg"></a>
<a href="https://opencollective.com/fakerjs/backer/3/website" target="_blank"><img src="https://opencollective.com/fakerjs/backer/3/avatar.svg"></a>
<a href="https://opencollective.com/fakerjs/backer/4/website" target="_blank"><img src="https://opencollective.com/fakerjs/backer/4/avatar.svg"></a>
<a href="https://opencollective.com/fakerjs/backer/5/website" target="_blank"><img src="https://opencollective.com/fakerjs/backer/5/avatar.svg"></a>
<a href="https://opencollective.com/fakerjs/backer/6/website" target="_blank"><img src="https://opencollective.com/fakerjs/backer/6/avatar.svg"></a>
<a href="https://opencollective.com/fakerjs/backer/7/website" target="_blank"><img src="https://opencollective.com/fakerjs/backer/7/avatar.svg"></a>
<a href="https://opencollective.com/fakerjs/backer/8/website" target="_blank"><img src="https://opencollective.com/fakerjs/backer/8/avatar.svg"></a>
<a href="https://opencollective.com/fakerjs/backer/9/website" target="_blank"><img src="https://opencollective.com/fakerjs/backer/9/avatar.svg"></a>
<a href="https://opencollective.com/fakerjs/backer/10/website" target="_blank"><img src="https://opencollective.com/fakerjs/backer/10/avatar.svg"></a>
<a href="https://opencollective.com/fakerjs/backer/11/website" target="_blank"><img src="https://opencollective.com/fakerjs/backer/11/avatar.svg"></a>
<a href="https://opencollective.com/fakerjs/backer/12/website" target="_blank"><img src="https://opencollective.com/fakerjs/backer/12/avatar.svg"></a>
<a href="https://opencollective.com/fakerjs/backer/13/website" target="_blank"><img src="https://opencollective.com/fakerjs/backer/13/avatar.svg"></a>
<a href="https://opencollective.com/fakerjs/backer/14/website" target="_blank"><img src="https://opencollective.com/fakerjs/backer/14/avatar.svg"></a>
<a href="https://opencollective.com/fakerjs/backer/15/website" target="_blank"><img src="https://opencollective.com/fakerjs/backer/15/avatar.svg"></a>
<a href="https://opencollective.com/fakerjs/backer/16/website" target="_blank"><img src="https://opencollective.com/fakerjs/backer/16/avatar.svg"></a>
<a href="https://opencollective.com/fakerjs/backer/17/website" target="_blank"><img src="https://opencollective.com/fakerjs/backer/17/avatar.svg"></a>
<a href="https://opencollective.com/fakerjs/backer/18/website" target="_blank"><img src="https://opencollective.com/fakerjs/backer/18/avatar.svg"></a>
<a href="https://opencollective.com/fakerjs/backer/19/website" target="_blank"><img src="https://opencollective.com/fakerjs/backer/19/avatar.svg"></a>
<a href="https://opencollective.com/fakerjs/backer/20/website" target="_blank"><img src="https://opencollective.com/fakerjs/backer/20/avatar.svg"></a>
<a href="https://opencollective.com/fakerjs/backer/21/website" target="_blank"><img src="https://opencollective.com/fakerjs/backer/21/avatar.svg"></a>
<a href="https://opencollective.com/fakerjs/backer/22/website" target="_blank"><img src="https://opencollective.com/fakerjs/backer/22/avatar.svg"></a>
<a href="https://opencollective.com/fakerjs/backer/23/website" target="_blank"><img src="https://opencollective.com/fakerjs/backer/23/avatar.svg"></a>
<a href="https://opencollective.com/fakerjs/backer/24/website" target="_blank"><img src="https://opencollective.com/fakerjs/backer/24/avatar.svg"></a>
<a href="https://opencollective.com/fakerjs/backer/25/website" target="_blank"><img src="https://opencollective.com/fakerjs/backer/25/avatar.svg"></a>
<a href="https://opencollective.com/fakerjs/backer/26/website" target="_blank"><img src="https://opencollective.com/fakerjs/backer/26/avatar.svg"></a>
<a href="https://opencollective.com/fakerjs/backer/27/website" target="_blank"><img src="https://opencollective.com/fakerjs/backer/27/avatar.svg"></a>
<a href="https://opencollective.com/fakerjs/backer/28/website" target="_blank"><img src="https://opencollective.com/fakerjs/backer/28/avatar.svg"></a>
<a href="https://opencollective.com/fakerjs/backer/29/website" target="_blank"><img src="https://opencollective.com/fakerjs/backer/29/avatar.svg"></a>

## Sponsors

Become a sponsor and get your logo on our README on Github with a link to your site. [[Become a sponsor](https://opencollective.com/fakerjs#sponsor)]

<a href="https://opencollective.com/fakerjs/sponsor/0/website" target="_blank"><img src="https://opencollective.com/fakerjs/sponsor/0/avatar.svg"></a>
<a href="https://opencollective.com/fakerjs/sponsor/1/website" target="_blank"><img src="https://opencollective.com/fakerjs/sponsor/1/avatar.svg"></a>
<a href="https://opencollective.com/fakerjs/sponsor/2/website" target="_blank"><img src="https://opencollective.com/fakerjs/sponsor/2/avatar.svg"></a>
<a href="https://opencollective.com/fakerjs/sponsor/3/website" target="_blank"><img src="https://opencollective.com/fakerjs/sponsor/3/avatar.svg"></a>
<a href="https://opencollective.com/fakerjs/sponsor/4/website" target="_blank"><img src="https://opencollective.com/fakerjs/sponsor/4/avatar.svg"></a>
<a href="https://opencollective.com/fakerjs/sponsor/5/website" target="_blank"><img src="https://opencollective.com/fakerjs/sponsor/5/avatar.svg"></a>
<a href="https://opencollective.com/fakerjs/sponsor/6/website" target="_blank"><img src="https://opencollective.com/fakerjs/sponsor/6/avatar.svg"></a>
<a href="https://opencollective.com/fakerjs/sponsor/7/website" target="_blank"><img src="https://opencollective.com/fakerjs/sponsor/7/avatar.svg"></a>
<a href="https://opencollective.com/fakerjs/sponsor/8/website" target="_blank"><img src="https://opencollective.com/fakerjs/sponsor/8/avatar.svg"></a>
<a href="https://opencollective.com/fakerjs/sponsor/9/website" target="_blank"><img src="https://opencollective.com/fakerjs/sponsor/9/avatar.svg"></a>
<a href="https://opencollective.com/fakerjs/sponsor/10/website" target="_blank"><img src="https://opencollective.com/fakerjs/sponsor/10/avatar.svg"></a>
<a href="https://opencollective.com/fakerjs/sponsor/11/website" target="_blank"><img src="https://opencollective.com/fakerjs/sponsor/11/avatar.svg"></a>
<a href="https://opencollective.com/fakerjs/sponsor/12/website" target="_blank"><img src="https://opencollective.com/fakerjs/sponsor/12/avatar.svg"></a>
<a href="https://opencollective.com/fakerjs/sponsor/13/website" target="_blank"><img src="https://opencollective.com/fakerjs/sponsor/13/avatar.svg"></a>
<a href="https://opencollective.com/fakerjs/sponsor/14/website" target="_blank"><img src="https://opencollective.com/fakerjs/sponsor/14/avatar.svg"></a>
<a href="https://opencollective.com/fakerjs/sponsor/15/website" target="_blank"><img src="https://opencollective.com/fakerjs/sponsor/15/avatar.svg"></a>
<a href="https://opencollective.com/fakerjs/sponsor/16/website" target="_blank"><img src="https://opencollective.com/fakerjs/sponsor/16/avatar.svg"></a>
<a href="https://opencollective.com/fakerjs/sponsor/17/website" target="_blank"><img src="https://opencollective.com/fakerjs/sponsor/17/avatar.svg"></a>
<a href="https://opencollective.com/fakerjs/sponsor/18/website" target="_blank"><img src="https://opencollective.com/fakerjs/sponsor/18/avatar.svg"></a>
<a href="https://opencollective.com/fakerjs/sponsor/19/website" target="_blank"><img src="https://opencollective.com/fakerjs/sponsor/19/avatar.svg"></a>
<a href="https://opencollective.com/fakerjs/sponsor/20/website" target="_blank"><img src="https://opencollective.com/fakerjs/sponsor/20/avatar.svg"></a>
<a href="https://opencollective.com/fakerjs/sponsor/21/website" target="_blank"><img src="https://opencollective.com/fakerjs/sponsor/21/avatar.svg"></a>
<a href="https://opencollective.com/fakerjs/sponsor/22/website" target="_blank"><img src="https://opencollective.com/fakerjs/sponsor/22/avatar.svg"></a>
<a href="https://opencollective.com/fakerjs/sponsor/23/website" target="_blank"><img src="https://opencollective.com/fakerjs/sponsor/23/avatar.svg"></a>
<a href="https://opencollective.com/fakerjs/sponsor/24/website" target="_blank"><img src="https://opencollective.com/fakerjs/sponsor/24/avatar.svg"></a>
<a href="https://opencollective.com/fakerjs/sponsor/25/website" target="_blank"><img src="https://opencollective.com/fakerjs/sponsor/25/avatar.svg"></a>
<a href="https://opencollective.com/fakerjs/sponsor/26/website" target="_blank"><img src="https://opencollective.com/fakerjs/sponsor/26/avatar.svg"></a>
<a href="https://opencollective.com/fakerjs/sponsor/27/website" target="_blank"><img src="https://opencollective.com/fakerjs/sponsor/27/avatar.svg"></a>
<a href="https://opencollective.com/fakerjs/sponsor/28/website" target="_blank"><img src="https://opencollective.com/fakerjs/sponsor/28/avatar.svg"></a>
<a href="https://opencollective.com/fakerjs/sponsor/29/website" target="_blank"><img src="https://opencollective.com/fakerjs/sponsor/29/avatar.svg"></a>
