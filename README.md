# betsol-ng-intl-tel-input


This module for Angular.js (`^1.8.0`) provides integration
for the great [intl-tel-input][intl-tel-input] jQuery plugin (version 17 is supported).

Please feel free to investigate [the original plugin][intl-tel-input]
for mode details, [features][intl-tel-input-features] and
[configuration][intl-tel-input-options].

> —» [DEMO][index.html] «—


## Installation

### Install integration library with `npm`

- `npm i --save betsol-ng-intl-tel-input`


### Add integration library to your page

Make sure, that module is added to your page either as a part of automatically built bundle
or manually using the code like this:

``` html
<script src="../betsol-ng-intl-tel-input/betsol-ng-intl-tel-input.js"></script>
```


### Add dependency in your application's module definition

``` javascript
var application = angular.module('application', [
  // ...
  'betsol.intlTelInput'
]);
```

### Introduce the directive

To add the plugin to any input field please use the `intl-tel-input` directive:

`<input type="tel" ng-model="user.phoneNumber" intl-tel-input>`


### Original plugin

This module depends on [intl-tel-input][intl-tel-input] plugin to operate.
If you installed the module using *npm*, then the dependency will be installed automatically,
and if your are using some automated build tool, it will probably be added to your bundle.

In other cases make sure to install it manually using the [following guide][intl-tel-input-install].


## Configuration

### Global

You can configure the plugin by changing the global object `intlTelInputOptions`.
This will apply specified changes across all plugin instances in your application.
All configuration options could be found in the [original plugin documentation][intl-tel-input-options].

#### Global Configuration Example

```javascript
angular
  .module('app', ['betsol.intlTelInput'])
  .config(function (intlTelInputOptions) {
    angular.extend(intlTelInputOptions, {
      nationalMode: false,
      utilsScript: '/vendor/intl-tel-input/utils.js',
      defaultCountry: 'auto',
      preferredCountries: ['ru', 'kz'],
      autoFormat: true,
      autoPlaceholder: true
    });
  })
;
```

### Custom instance configuration

You can configure each input field individually by
specifying the configuration options via `intl-tel-input-options` attribute.

#### Instance Configuration Example

```html
<input
    type="tel"
    ng-model="user.phoneNumber"
    intl-tel-input
    intl-tel-input-options="{ excludeCountries: ['us', 'de'] }"
>
```

## API

You can use `intl-tel-input-controller` attribute to specify an object
that will be populated with the directive's API functions.

### API Usage Example

```javascript
angular
  .module('app', ['betsol.intlTelInput'])
  .controller('MyCtrl', function ($scope) {
    $scope.myIntlTelInputCtrl;
    $scope.changeCountryToRussia = function () {
      $scope.myIntlTelInputCtrl.setCountry('ru');
    };
  })
;
```

```html
<input
    type="tel"
    ng-model="user.phoneNumber"
    intl-tel-input
    intl-tel-input-controller="myIntlTelInputCtrl"
>
<button ng-click="changeCountryToRussia()">
    Change Country to Russia
</button>
```


### List of Supported API Functions:

- `setCountry({string} countryCode)`

### Phone number validator

This directive will add `phoneNumber` validator to the underlying model controller.
You can use it to display validation errors.

#### Validation Example

```
<span ng-show="formName.inputName.$error.phoneNumber">
    Please enter a correct phone number!
</span>
```


## Changelog

Please see the [changelog][changelog] for list of changes.
