# CertainTLS
A “trusted certificate checker” … which would determine whether a device’s OS and/or applications is trusting root TLS certs it shouldn’t. ![Automated tests](https://github.com/certaintls/certaintls.app/workflows/CI/badge.svg)

## Problem statement
HTTPS MiTM Online HTTPS communications via a browser, e.g. with an online service such as Facebook or Google, are normally end-to-end-encrypted via TLS. But the security this system provides depends on the TLS cert being “good,” which in turn depends on it being “anchored” to a trusted cert—which depends on the anchor being trustworthy. But if the end user is trusting a “bad” cert, a monster-in-the-middle attack (MiTM) will be able to read and decrypt her web traffic, inject fake content in real time, and harvest credentials, thereby nullifying the security the end user believed she had. How can a user know whether the certs she’s trusting are all “good”?

## How does CertainTLS work?
CertainTLS consists of two parts: a multi-platform app, and a back-end server. The server periodically aggregates the root certificates from the [Google](https://android.googlesource.com/platform/system/ca-certificates/+/master/files/) ![Android pipeline](https://github.com/certaintls/certaintls.app/workflows/Android%20cron/badge.svg), [Apple](https://support.apple.com/en-us/HT210770) ![MacOS pipeline](https://github.com/certaintls/certaintls.app/workflows/MacOS%20cron/badge.svg), [Microsoft](https://ccadb-public.secure.force.com/microsoft/IncludedCACertificateReportForMSFT) ![Windows pipline](https://github.com/certaintls/certaintls.app/workflows/Windows%20cron/badge.svg) and [Mozilla](https://ccadb-public.secure.force.com/mozilla/IncludedCACertificateReport) ![Mozilla pipeline](https://github.com/certaintls/certaintls.app/workflows/Mozilla%20cron/badge.svg) certificate authority programs. CertainTLS's back end then analyze these certificates and mark the ones from the issuing companies in the countries whose [Freedom in the World](https://freedomhouse.org/countries/freedom-world/scores) score lower than **40** as **Untrustworthy**. The CertainTLS app scans both the root certificates shipped by the OS and user-installed trusted root certificates, then validates each of them against the CertainTLS back end's "source of truth," and displays the result in the app, i.e. flagging root certs which are being trusted but maybe shouldn't be. The app also supports OSes' specific way to distrust certificates. Due to different security models and the app's limitation as third-party tool in different OSes, the CertainTLS app currently supports Android, MacOS, and Windows (but not iOS), and the app's functionality on each platform differs slightly. To see exactly what features are supported on each platform, please [see](https://github.com/certaintls/certaintls.app/wiki/Supported-Features-on-Different-OS).

## Download the app
<a href='https://play.google.com/store/apps/details?id=app.certaintls.flutter&pcampaignid=pcampaignidMKT-Other-global-all-co-prtnr-py-PartBadge-Mar2515-1'><img alt='Get it on Google Play' src='https://play.google.com/intl/en_us/badges/static/images/badges/en_badge_web_generic.png' height='80px'/></a>

## Contribution guidline
You are invited to contribute new features, fixes, or updates, large or small; we are always thrilled to receive pull requests, and do our best to process them as fast as we can. Besides the code, a reproduciable bug report or documentation improvement is also great contribution. To start filing bugs or asking questions, please use [Github issues](https://github.com/certaintls/certaintls.app/issues) of the Certaintls App.

## Technical documentation
* [CertainTLS App](https://github.com/certaintls/certaintls.app/wiki)
* [CertainTLS Server](https://github.com/certaintls/certaintls.backend/wiki)

## Privacy Policy

## Sponsorship
The CertainTLS project is sponsored by [Counterpart International](https://www.counterpart.org/). Counterpart International is an NGO working in the international development sector. One of Counterpart International ’s projects, the ISC, enhances internet freedom by improving the defensive cybersecurity capabilities of local partners in developing countries.
