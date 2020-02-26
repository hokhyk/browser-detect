## Browser Detection v4 by _[hisorange](https://hisorange.me)_

[![Latest Stable Version](https://poser.pugx.org/hisorange/browser-detect/v/stable)](https://packagist.org/packages/hisorange/browser-detect)
[![Build Status](https://travis-ci.org/hisorange/browser-detect.svg?branch=stable)](https://travis-ci.org/hisorange/browser-detect)
[![Coverage Status](https://coveralls.io/repos/github/hisorange/browser-detect/badge.svg)](https://coveralls.io/github/hisorange/browser-detect)
[![Total Downloads](https://poser.pugx.org/hisorange/browser-detect/downloads)](https://packagist.org/packages/hisorange/browser-detect)
[![License](https://poser.pugx.org/hisorange/browser-detect/license)](https://packagist.org/packages/hisorange/browser-detect)

Easy to use package to identify the visitor's browser details and device type.
Magic is **not** involved the results are generated by multiple well tested and developed packages.
Supporting **every laravel** version between **4.0 &raquo; 6.5**, also tested on **every PHP** version between **5.6 &raquo; 7.3**.

### How to install

---

```sh
composer require hisorange/browser-detect
```

Yep, it's ready to be used by You! ^.^

### How to use

---

In Your code just call the **Browser** facade:

```php
use Browser;

// Determine the user's device type is simple as this:
Browser::isMobile();
Browser::isTablet();
Browser::isDesktop();

// Every wondered if it is a bot who loading Your page?
if (Browser::isBot()) {
    echo 'No need to wonder anymore!';
}

// Check for common vendors.
if (Browser::isFirefox() || Browser::isOpera()) {
    $response .= '<script src="firefox-fix.js"></script>';
}

// Sometime You may want to serve different content based on the OS.
if (Browser::isAndroid()) {
    $response .= '<a>Install our Android App!</a>';
} elseif (Browser::isMac() && Browser::isMobile()) {
    $response .= '<a>Install our iOS App!</a>';
}
```

Even in Your blade templates:

```blade
@mobile
    <p>This is the MOBILE template!</p>
    @include('your-mobile-template')
@endmobile

@tablet
    <p>This is the TABLET template!</p>
    <link rel="stylesheet" href="tablet.css" title="Reduce the page size, load what the user need">
@endtablet

@desktop
    <p>This is the DESKTOP template!</p>
@enddesktop

{-- Every result key is supported --}
@browser('isBot')
    <p>Bots are identified too :)</p>
@endbrowser
```

Easy peasy, ain't it?

### Version support

---

The following matrix is has been continuously tested by the great and awesome [Travis CI](https://travis-ci.org/hisorange)!

|    -----    | Browser Detect 1.x | Browser Detect 2.x | Browser Detect 3.x | Browser Detect 4.x |
| :---------: | :----------------: | :----------------: | :----------------: | :----------------: |
| Laravel 4.x |      &#10003;      |      &#10003;      |         -          |         -          |
| Laravel 5.x |         -          |      &#10003;      |      &#10003;      |         -          |
| Laravel 6.x |         -          |         -          |         -          |      &#10003;      |

Since 2013 the package runs tests on every possible PHP / Laravel version matrix.

### Available API calls

---

Every call on the **Browser** facade is proxied to a result object, so the following information are available on Your result too, where You can use the \[array\] syntax to access them.

| Call                                    | Response                                                                | Internal Type |
| :-------------------------------------- | :---------------------------------------------------------------------- | :-----------: |
| Browser::userAgent()                    | Current visitor's HTTP_USER_AGENT string.                               |  _(string)_   |
| Browser::isMobile()                     | Is this a mobile device.                                                |  _(boolean)_  |
| Browser::isTablet()                     | Is this a tablet device.                                                |  _(boolean)_  |
| Browser::isDesktop()                    | Is this a desktop computer.                                             |  _(boolean)_  |
| Browser::isBot()                        | Is this a crawler / bot.                                                |  _(boolean)_  |
| **Browser related functions**           |                                                                         |               |
| Browser::browserName()                  | Browser's human friendly name like Firefox 3.6, Chrome 42.              |  _(string)_   |
| Browser::browserFamily()                | Browser's vendor like Chrome, Firefox, Opera.                           |  _(string)_   |
| Browser::browserVersion()               | Browser's human friendly version string.                                |  _(string)_   |
| Browser::browserVersionMajor()          | Browser's [semantic](https://semver.org/) major version.                |  _(integer)_  |
| Browser::browserVersionMinor()          | Browser's [semantic](https://semver.org/) minor version.                |  _(integer)_  |
| Browser::browserVersionPatch()          | Browser's [semantic](https://semver.org/) patch version.                |  _(integer)_  |
| Browser::browserEngine()                | Browser's engine like: Blink, WebKit, Gecko.                            |  _(string)_   |
| **Operating system related functions**  |                                                                         |               |
| Browser::platformName()                 | Operating system's human friendly name like Windows XP, MacOS 10.       |  _(string)_   |
| Browser::platformFamily()               | Operating system's vendor like Linux, Windows, MacOS.                   |  _(string)_   |
| Browser::platformVersion()              | Operating system's human friendly version like XP, Vista, 10.           |  _(integer)_  |
| Browser::platformVersionMajor()         | Operating system's [semantic](https://semver.org/) major version.       |  _(integer)_  |
| Browser::platformVersionMinor()         | Operating system's [semantic](https://semver.org/) minor version.       |  _(integer)_  |
| Browser::platformVersionPatch()         | Operating system's [semantic](https://semver.org/) patch version.       |  _(integer)_  |
| **Operating system extended functions** |                                                                         |               |
| Browser::isWindows()                    | Is this a windows operating system.                                     |  _(boolean)_  |
| Browser::isLinux()                      | Is this a linux based operating system.                                 |  _(boolean)_  |
| Browser::isMac()                        | Is this an iOS or Mac based operating system.                           |  _(boolean)_  |
| Browser::isAndorid()                    | Is this an Andorid operating system.                                    |  _(boolean)_  |
| **Device related functions**            |                                                                         |               |
| Browser::deviceFamily()                 | Device's vendor like Samsung, Apple, Huawei.                            |  _(string)_   |
| Browser::deviceModel()                  | Device's brand name like iPad, iPhone, Nexus.                           |  _(string)_   |
| Browser::mobileGrade()                  | Device's mobile grade in scale of A,B,C for performance.                |  _(string)_   |
| **Browser vendor related functions**    |                                                                         |               |
| Browser::isChrome()                     | Is this a chrome browser.                                               |  _(boolean)_  |
| Browser::isFirefox()                    | Is this a firefox browser.                                              |  _(boolean)_  |
| Browser::isOpera()                      | Is this an opera browser.                                               |  _(boolean)_  |
| Browser::isSafari()                     | Is this a safari browser.                                               |  _(boolean)_  |
| Browser::isIE()                         | Checks if the browser is an some kind of Internet Explorer (or Trident) |  _(boolean)_  |
| Browser::isIEVersion()                  | Compares to a given IE version                                          |  _(boolean)_  |
| Browser::isEdge()                       | Is this a microsoft edge browser.                                       |  _(boolean)_  |

### Advanced Usage Information

---

The code is designed to be an easy to use style,
so every call You make on the **Browser** facade will access the result object and get the data for You,
but You can parse agents other then the current user's.

```php
// When You call the detect function You will get a result object, from the current user's agent.
$result = Browser::detect();

// If You wana get browser details from a user agent other then the current user call the parse function.
$result = Browser::parse('Opera/9.80 (Windows NT 6.0) Presto/2.12.388 Version/12.14');
```

Worthy notion! The parser only parsing each user agent string once and then caches it,
it uses an inmemory runtime cache for multiple calls in a single page load;
And it will use the application's cache to persist the result for a week or so,
this should provide You with a sufficient caching mechanism so the detection will
cost less than **0.02 millisecond**, this was tested with a 80,000 fake visit.

### Changelog

---

See the detailed changes in the [CHANGELOG](CHANGELOG.md) file.
