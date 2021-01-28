---
title: "announcing lettre 0.10"
description: "Lettre 0.10 has been released"
date: "2020-02-01"
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

Since 0.9 release in March 2019, a lot of changes were made. Key
improvements are:

* replacement of the email builder implementation (which was based on `rust-email`)
  by a new one based on the `emailmessage` crate. The main goal was to provide
  sane encoding and multipart with a simple implementation
* merge of the `lettre_email` crate into `lettre`
* add more features to the crate to give more control on dependencies
* add the option to use `rustls` for TLS
* improve parsing of server responses
* move CI from Travis to Github actions
* async support (using `async-std` or `tokio`)
* initial support for encrypted and signed messages

0.10 has counted 5 alpha releases since May 2020, is already
quite widely used and is already thought to be more
reliable than 0.9.

#### the road to 1.0

0.10 is a first step on the road to 1.0, as all
major features required for a stable version are implemented.

We'd love to hear your feedbacks about 0.10 design and APIs
to be able to fix problems in lettre before 1.0.

#### community

lettre was built 45 contributors since its creation,
including 25 for 0.10. Thanks a lot for your help!

The 0.10 release was made possible by the amazing work of [@paolobarbolini](https://github.com/paolobarbolini)
who joined the maintainer team this year, and lead the development efforts since.
Issue and pull requests response time has considerably lowered too,
making lettre a more welcoming project for contributors and users.
