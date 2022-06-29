---
title: "Announcing lettre 0.10"
description: "lettre 0.10.0 has been released"
date: "2022-06-29"
---

We are pleased to announce the release of the (long awaited) 0.10 version of lettre, an email client for the Rust programming language.
lettre allows sending emails from Rust applications, focusing on ease of use, secure
defaults and modern features (like support for full internationalization).
It does not aim at implementing email RFCs extensively, but only what is necessary for our needs.

lettre provides a type-safe email builder, several transports, tls support with `rustls` and `native-tls` and async support with `tokio` and `async-std`.

lettre is now used by many projects, including
[crates.io](https://github.com/rust-lang/crates.io/blob/master/src/email.rs) itself!

## Changes

Since the 0.9 release in March 2019, more than three years ago, a lot of changes have been made.
Key improvements are:

### New message builder

The message implementation has been completely replaced. The goal was to provide correct encoding
and powerful multipart features.

The message implementation, previously in the `lettre_email` crate, has been merged into `lettre`.

### DKIM support

It is now possible to sign emails using DKIM.

### Async support

Transports now have `async-std` and `tokio` support for async email sending.

### Features and dependencies

We added a lot of control over which features can be enabled

#### rustls support

In addition to `native-tls`, lettre now supports `rustls` for encrypted SMTP connections.

### File transport

The file transport allows storing emails to disk, and now uses the standard `.eml`
format instead of `json`. This format stores the email with the original
headers and body, and can be read by standard email applications like Thunderbird.
`.eml` files can also be read back, making it possible to send them later.

### Miscellaneous

* The number of publicly exposed dependencies has been reduced, improving API stability
* A lot of CI improvements, including moving to Github actions
* The [previous doc site](https://lettre.rs/0.9/) has been merged into the crate documentation
* MSRV is now 1.56.

Read the [change log](https://github.com/lettre/lettre/blob/master/CHANGELOG.md#v0100) for more details.

## Upgrading

0.10 has counted 5 alpha, 4 beta and 7 rc releases since May 2020, and is already
widely used.
Upgrade from 0.9 should be pretty straightforward (except for complex MIME messages).

To migrate, update your `Cargo.toml` to:

```toml
[dependencies]
lettre = "0.10.0"
```

Migration notes:

* The `lettre_email` crate has been merged into `lettre`. To migrate, replace `lettre_email` with `lettre::message` and make sure to enable the builder feature (it's enabled by default). The builder interface has been rewritten, so you will have to migrate your existing code to the new methods.
* `SendableEmail` has been renamed to `Message` and `MessageBuilder` produces it directly. To migrate, rename `SendableEmail` to `Message`.
* The `serde-impls` feature has been renamed to `serde`. To migrate, rename the feature.
* `FileTransport` writes emails into `.eml` instead of `.json`

If you need help or advice, please take a look at the [examples](https://github.com/lettre/lettre/tree/master/examples) or start a [discussion](https://github.com/lettre/lettre/discussions)
in the repository.

## Community

The 0.10 release was more specifically made possible by the involvement of [paolobarbolini](https://github.com/paolobarbolini),
who joined the maintainer team and now leads the project.
In particular, issue and pull requests response times have been considerably lowered,
making lettre a more welcoming project for users and contributors.

Special thanks to all contributor to this release since 0.9, in particular:

* Alexander Jackson ([alexander-jackson](https://github.com/alexander-jackson)) for improving documentation
* Alex Feldman-Crough ([afldcr](https://github.com/afldcr)) for allowing to convert a `Message` back to `MessageBuilder`
* Alex Wennerberg ([alexwennerberg](https://github.com/alexwennerberg)) for replacing `rand` by `fastrand`
* André Cruz ([edevil](https://github.com/edevil)) for adding `email_address` to validate email addresses
* azul ([azul](https://github.com/azul)) for switching to `eml` format in `FileTransport`
* Benjamin Beckwith ([bnbeckwith](https://github.com/bnbeckwith)) for documentation improvements
* Christopher Vittal ([chrisvittal](https://github.com/chrisvittal)) for improving email address handling
* David Krasnitsky ([DK26](https://github.com/DK26)) for improving error messages
* Dirkjan Ochtman ([djc](https://github.com/djc)) for improving SMTP error messages
* dvermd ([dvermd](https://github.com/dvermd)) for improving credentials handling
* facklambda ([facklambda](https://github.com/facklambda)) for adding troubleshooting documentation
* Federico Guerinoni ([guerinoni](https://github.com/guerinoni)) for improving the documentation
* Filip Gospodinov ([toxeus](https://github.com/toxeus)) for improvement of email transports
* Gaëtan Duchaussois ([gaetronik](https://github.com/gaetronik)) for their work on DKIM support
* Manuel Ghizzoni  ([ghizzo01](https://github.com/ghizzo01)) for improving the transports
* Hari Konomi ([konomith](https://github.com/konomith)) for adding proper connection pool closing
* Jacob Halsey ([jacob-pro](https://github.com/jacob-pro)) for allowing to set the local IP address to connect from
* Jacob Mischka ([jacobmischka](https://github.com/jacobmischka)) for the `mime` feature flag
* James Hillyerd ([jhillyerd](https://github.com/jhillyerd)) for their documentation contribution
* Julien Blatecky ([julien1619](https://github.com/julien1619)) for adding `Content-ID` header
* [Jupp56](https://github.com/Jupp56) for fixing the README example
* Kevin Cox ([kevincox]([](https://github.com/kevincox)) for their work on DKIM support and headers encoding
* Manuel Pelloni ([manuelpelloni](https://github.com/manuelpelloni)) for various refactorings and improving the documentation
* [RotationMatrix](https://github.com/RotationMatrix) for improving the examples
* Sven-Hendrik Haase ([svenstaro](https://github.com/svenstaro)) for improving the `StubTransport`
* Tim Anderson ([timando](https://github.com/timando)) for adding encrypted and signed multipart emails support
* [TornaxO7](https://github.com/TornaxO7) for improvement of `Content-Type` header
* Vincent Breitmoser ([Valodim](https://github.com/Valodim)) for fixing date format in headers
