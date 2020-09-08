---
title: "towards lettre 1.0"
description: "towards lettre 1.0"
date: "2020-08-24"
---

#### what is lettre?

lettre is an email client for Rust programs, to allow easily sending emails from Rust
applications with the following focuses:

* ease of use, without particular knowledge about email
* secure by default
* modern (support for full internationalization)

non-goals:

* implementing email RFCs extensively. The goal is to target a modern and safe subset needed to
  send emails today, with a nice API (i.e. UTF-8 only, etc.). Particularly, lettre
  currently cannot parse emails.

#### changes in 0.10

* replacement of the email builder implementation (which was based on `rust-email`)
  by a new one based on the `emailmessage` crate. To main goal is to provide
  sane encoding and multipart with a simple implementation (no message parsing).
  `email` API requires email knowledge and maintaining a facade makes things
  harder.
* merge of the `lettre_email` crate into `lettre`, and more features to allow disabling most features.
* add the option to use `rustls` for TLS.
* improved parsing of server responses.
* moved CI from Travis to Github actions.
* async support (based on `async-std` and `tokio`).

#### the road to 1.0

lettre is now used by several projects, including crates.io!
It will be good to have a stable basis for the future.

The plan is that 0.10 is the release preparing the 1.0 in the following months.
I'd also want to add more real-world automated testing with actual mail servers.

#### looking for contributors and maintainers

email is not an easy ..., because if a lot of people want to use it,
few of them want to work on email libraries (as opposed to... let's say http!),
as it is generally assumed to be boring legacy stuffed with old compatibility tricks
and ... (it is).

But we have good news, [@paolobarbolini](https://github.com/paolobarbolini) recently joined me
((@amousset)[https://github.com/amousset]) in the maintainer team, so development, bug fixes
and PR reviews should work better.

lettre is open to contributions, and I would be particularly glad to find
someone interested in maintaining it.

The `lettre` organization is also open for hosting anything
related to email in Rust.

#### background: a bit of history

The `lettre` crate was previously named [`smtp`](https://crates.io/crates/smtp). It [started](https://github.com/lettre/lettre/commit/270efd193a11e66dce14700a50d3c42c12e725bc) in early 2014 (before cargo, Rust 1.0, etc.).

The first goal was to start a toy project as a pretext to learn Rust. I started with an `smtp` implementation after seeing there was no existing implementation in Rust. Originally, the project aimed at implementing the `SMTP` protocol for client and server.

In 2016, the goal changed, and specialized to email client (as I did not see much use in another SMTP server may it be written in Rust). The project also moved away from "just SMTP" to email client, and was renamed to lettre at this time. Why `lettre`? After some time looking for a fitting name, not already taken by email-related software, I ended up just taking the the French word for "letter"!
