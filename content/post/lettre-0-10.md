---
title: "announcing lettre 0.10"
description: "lettre 0.10 has been released"
date: "2020-05-13"
draft: true
---

We are pleased to announce the 0.10 release of lettre, an email client for Rust programs.
lettre allows sending emails from Rust applications, focusing on ease of use, security by
default and modern features (like support for full internationalization).
It does not aim at implementing email RFCs extensively, but only what is necessary for our needs.

lettre provides a type-safe email builder, several transports, tls support with `rustls` and `native-tls`
and async support with `tokio` and `async-std`.

lettre is now used by many projects, including
[crates.io](https://github.com/rust-lang/crates.io/blob/master/src/email.rs) itself!

#### changes in 0.10

Since 0.9 release in March 2019, more than two years ago, a lot of changes were made. Key
improvements are:

* replace of the email builder implementation (which was based on `rust-email`)
  by a new one. The main goal was to provide   sane encoding and multipart with a simple implementation
* merge the `lettre_email` crate into `lettre`
* add more features to the crate to give more control on dependencies
* add the option to use `rustls` for TLS
* improve parsing of server responses
* move CI from Travis to Github actions
* add async support (using `async-std` or `tokio`)
* add initial support for encrypted and signed messages

0.10 has counted 5 alpha releases since May 2020, is already
quite widely used and is already thought to be more
reliable than 0.9.

#### upgrade

Upgrade from 0.9 is pretty straightforward, except for complex MIME messages.

If you need help or advice, please start a [discussion](https://github.com/lettre/lettre/discussions)
in the repository.

#### road to 1.0

0.10 is a first step on the road to 1.0, as all
major features required for a stable version are now implemented.

We'd love to hear your feedback about 0.10 design and APIs
to be able to improve lettre's API before 1.0.

#### community

lettre was built by 45 contributors since its creation,
including 25 for 0.10 only. Thanks a lot for your help!

The 0.10 release was made possible by the amazing work of [@paolobarbolini](https://github.com/paolobarbolini)
who joined the maintainer team this year,
and lead the development efforts for the end of 0.10.
Issue and pull requests response time has considerably lowered too,
making lettre a more welcoming project for contributors and users.

The `lettre` organization is open for other projects related to email in Rust.
