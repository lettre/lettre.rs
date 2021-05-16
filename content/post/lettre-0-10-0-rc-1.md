---
title: "Announcing lettre 0.10.0-rc.1"
description: "lettre 0.10.0-rc.1 has been released"
date: "2021-05-16"
---

We are pleased to announce the first release candidate of the next version of lettre, an email client for Rust programs.
lettre allows sending emails from Rust applications, focusing on ease of use, security by
default and modern features (like support for full internationalization).
It does not aim at implementing email RFCs extensively, but only what is necessary for our needs.

lettre provides a type-safe email builder, several transports, tls support with `rustls` and `native-tls` and async support with `tokio` and `async-std`.

lettre is now used by many projects, including
[crates.io](https://github.com/rust-lang/crates.io/blob/master/src/email.rs) itself!

#### Changes

Since 0.9 release in March 2019, more than two years ago, a lot of changes were made.
Key improvements are:

**New message builder**

The message implementation has been completely replaced. The goals was to provide correct encoding
and powerful multipart features.

The message implementation, previously in the `lettre_email` crate, has been merged into `lettre`.

**Async support**

Transports now have `async-std` and `tokio` support for async email sending.

**Features and dependencies**

We added a lot of control over enabled features has been

**rustls support**

In addition to `native-tls`, lettre now supports `rustls` for encrypted SMTP transport.

**File transport**

This file transport which allows storing emails to disk instead of sending them, now uses a more standard `.eml`
formal instead of `json`, and is now able to read the message to send them later.

**Miscellaneous**

* The number of publicly exposed dependencies has been reduced, to improve API stability
* A lot of CI improvements, including moving to Github actions
* The [previous doc site](https://lettre.rs/0.9/) has been merged into the crate documentation
* MSRV is now 1.46.

Read the [change log](https://github.com/lettre/lettre/blob/master/CHANGELOG.md#v0100) for more details.

#### Upgrade

0.10 has counted 5 alpha and 4 beta releases since May 2020, is already
widely used and is thought to be more reliable than 0.9.
Upgrade from 0.9 should be pretty straightforward (except for complex MIME messages).

To migrate, update your `Cargo.toml` to:

```toml
[dependencies]
lettre = "0.10.0-rc.1"
```

Migration notes:

* The `lettre_email` crate has been merged into `lettre`. To migrate, replace `lettre_email` with `lettre::message` and make sure to enable the builder feature (it's enabled by default). The builder interface has been rewritten, so you will have to migrate your existing code to the new methods.
* `SendableEmail` has been renamed to `Email` and `EmailBuilder::build()` produces it directly. To migrate, rename `SendableEmail` to `Email`.
* The `serde-impls` feature has been renamed to `serde`. To migrate, rename the feature.
* `FileTransport` writes emails into `.eml` instead of `.json`

If you need help or advice, please start a [discussion](https://github.com/lettre/lettre/discussions)
in the repository.

#### Road to 1.0

0.10 is a first step on the road to 1.0, as most
major features required for a stable version are now implemented.

We'd love to hear your feedback about 0.10 design and APIs
to be able to improve lettre's API before 1.0.

#### Community

lettre was built by 48 contributors since its creation,
including 25 for 0.10 only. Thanks a lot for your help!

The 0.10 release was made possible by the great work of [@paolobarbolini](https://github.com/paolobarbolini)
who joined the maintainer team and did most of last year's improvements.
In particular, issue and pull requests response time has considerably lowered,
making lettre a more welcoming project for contributors and users.

Besides the mailer itself, the `lettre` organization is open for other projects related to email in Rust.
