# CertainTLS
A “trusted certificate checker” … which would determine whether a device’s OS and/or applications is trusting root TLS certs it shouldn’t. ![Automated tests](https://github.com/certaintls/certaintls.app/workflows/CI/badge.svg)

## Problem statement
Online HTTPS communications (e.g. via a browser) with an online service such as Facebook or Gmail are normally end-to-end-encrypted using TLS. But the security this system provides depends on the TLS public cert presented by the remote service being “good,” which in turn depends on it being “anchored” to a trusted cert—which depends on the anchor being trustworthy. But if the end user is trusting a “bad” root cert (for whatever reason), a monster-in-the-middle attack (MiTM) will be able to read and decrypt their web traffic, inject fake content in real time, and harvest credentials, thereby nullifying the security the end user believed they had. How can a user know whether the certs they're trusting are all “good”?

## How does CertainTLS work?
CertainTLS consists of two parts: a multi-platform app, and a back-end server. The server periodically aggregates the "canonical" root certificates from the [Google](https://android.googlesource.com/platform/system/ca-certificates/+/master/files/) ![Android pipeline](https://github.com/certaintls/certaintls.app/workflows/Android%20cron/badge.svg), [Apple](https://support.apple.com/en-us/HT210770) ![MacOS pipeline](https://github.com/certaintls/certaintls.app/workflows/MacOS%20cron/badge.svg), [Microsoft](https://ccadb-public.secure.force.com/microsoft/IncludedCACertificateReportForMSFT) ![Windows pipline](https://github.com/certaintls/certaintls.app/workflows/Windows%20cron/badge.svg) and [Mozilla](https://ccadb-public.secure.force.com/mozilla/IncludedCACertificateReport) ![Mozilla pipeline](https://github.com/certaintls/certaintls.app/workflows/Mozilla%20cron/badge.svg) certificate authority programs. CertainTLS's back end then analyzes these certificates and marks the ones from the issuing companies in the countries whose [Freedom in the World](https://freedomhouse.org/countries/freedom-world/scores) score's lower than **40** as **untrustworthy**. The CertainTLS app scans both the root certificates shipped by the OS and user-installed trusted root certificates, then validates each of them against the CertainTLS back end's "source of truth," and displays the result in the app, i.e. flagging root certs which are being trusted but maybe shouldn't be. The app also supports OSes' specific way to distrust certificates. Due to different security models and the app's limitation as a "third-party tool" in different OSes, CertainTLS currently supports Android, macOS, and Windows, but not (yet?) iOS, and the app's functionality on each platform differs slightly. For more information about which features are supported on each platform, please see [here](https://github.com/certaintls/certaintls.app/wiki/Supported-Features-on-Different-OS).

The impetus to develop CertainTLS came from *inter alia* the (allegedly Iranian) 2011 DigiNotar hack, China's 2015 Great Cannon (not a root cert problem but, more generally, an authoritarian government's willingness to force domestic private actors to compromise a foreign internet asset's integrity), and the 2019 middling (by the КНБ) of all access to ~250 key foreign sites (including Facebook and Gmail) by all netizens using Kazakhstan's biggest ISP in that country's capital—supposedly "a test," but, well ...

## Download the app
#### From the trusted distribution channel: (recommended):

<a href='https://play.google.com/store/apps/details?id=app.certaintls.flutter&pcampaignid=pcampaignidMKT-Other-global-all-co-prtnr-py-PartBadge-Mar2515-1'><img alt='Get it on Google Play' src='https://play.google.com/intl/en_us/badges/static/images/badges/en_badge_web_generic.png' height='80px'/></a>

#### From Github.com CertainTLS releases:
[Download directly](https://github.com/certaintls/certaintls.app/releases)

## Contribution guidline
You are invited to contribute new features, fixes, or updates, large or small; we are always thrilled to receive pull requests, and do our best to process them as fast as we can. Besides the code, a reproducible bug report or documentation improvement is also welcome. To start filing bugs or asking questions, please use the CertainTLS app's [Github issues](https://github.com/certaintls/certaintls.app/issues).

## Technical documentation
* [CertainTLS app](https://github.com/certaintls/certaintls.app/blob/master/README.md)
* [CertainTLS server](https://github.com/certaintls/certaintls.backend/blob/master/README.md)

## Privacy Policy

[Read the CertainTLS privacy policy](https://github.com/certaintls/certaintls/blob/master/PRIVACY.md#privacy-statement---certaintls)

## Sponsorship
CertainTLS' development was financed by the USAID-funded Information Safety & Capacity Project (ISC), a grant to [Counterpart International](https://www.counterpart.org/), an international NGO working in the civil society development sector. The ISC supports internet freedom by improving the defensive cybersecurity capabilities of local partners (rights-defending activists, journalists) in developing countries.
