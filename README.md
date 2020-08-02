# CertainTLS
A “trusted certificate checker” … which would determine whether a device’s OS and/or applications is trusting TLS certs it shouldn’t.

## Problem statement
HTTPS MiTM Online HTTPS communications via a browser, e.g. with an online service such as Facebook or Google, are normally end-to-end-encrypted via TLS. But the security this system provides depends on the TLS cert being “good,” which in turn depends on it being “anchored” to a trusted cert—which depends on the anchor being trustworthy. But if the end user is trusting a “bad” cert, a monster-in-the-middle attack (MiTM) will be able to read and decrypt her web traffic, inject fake content in real time, and harvest credentials, thereby nullifying the security the end user believed she had. How can a user know whether the certs she’s trusting are all “good”?

## How does CertainTLS work?
CertainTLS consists two parts: A multi-platform app and a backend server. The server periodically aggregate the root certificates from the [Google](https://android.googlesource.com/platform/system/ca-certificates/+/master/files/), [Apple](https://support.apple.com/en-us/HT210770), [Microsfot](https://ccadb-public.secure.force.com/microsoft/IncludedCACertificateReportForMSFT) and [Mozilla](https://ccadb-public.secure.force.com/mozilla/IncludedCACertificateReport) certificate authority programs. CertainTLS backend then analyze these certificates and mark the ones from the issuing companies in the countries whose [Freedom in the World] score lower than **40** as **Untrustworthy**. The CertainTLS app scans both the root certificates shipped by the OS and user installed certificates, then validate each of them against the CertainTLS backend's source of truth, and display the result in the app. The app also supports OSes specific way to distrust certificates. Due to different security model and its limitation as third party tool in different OSes, the CertainTLS app currently supports Android, MacOS and Windows. The functionality on each platform may also differ due to the same limitations. To see exactly what features are supported on each platform, please [see](https://github.com/certaintls/certaintls.app/wiki/Supported-Features-on-Different-OS). 


## Privacy Policy

## Sponsorship
The CertainTLS project is sponsored by [Counterpart International](https://www.counterpart.org/). Counterpart International is an NGO working in the international development sector. One of Counterpart International ’s projects, the ISC, enhances internet freedom by improving the defensive cybersecurity capabilities of local partners in developing countries.
