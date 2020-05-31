---
title: "lettre 0.10"
description: "lettre 0.10 has been released"
date: "2020-04-01"
draft: true
---

## What is `lettre`?

Lettre provides an email client for Rust programs, to allow easily sending emails from Rust
applications with the following focuses

* Ease of use, without particular knowledge about email
* Secure by default
* Modern (support for full internationalization)

Non-goals:

* Implementing email RFCs extensively. The goal is to target a modern and safe subset needed to
  send emails today, with a nice API (i.e. UTF-8 only, etc.). Particularly, lettre
  currently cannot parse emails.

### Background

The `lettre` crate was previously named [`smtp`](https://crates.io/crates/smtp). It [started](https://github.com/lettre/lettre/commit/270efd193a11e66dce14700a50d3c42c12e725bc) in early 2014 (before cargo, Rust 1.0, etc.).

The first goal was to start a toy project as a pretext to learn Rust. I started with an `smtp` implementation after seeing there was no existing implementation in Rust. Originally, the project aimed at implementing the `SMTP` protocol for client and server.

In 2016, the goal changed, and specialized to email client (as I did not see much use in another SMTP server may it be written in Rust). The project also moved away from "just SMTP" to email client, and was renamed to lettre at this time. Why `lettre`? After some time looking for a fitting name, not already taken by email-related software, I ended up just taking the the French word for "letter"!

## Changes in 0.10

* Replacement of the email builder implementation (which was based on `rust-email`)
  by a new one based on the `emailmessage` crate. To main goal is to provide
  sane encoding and multipart with a simple implementation (no message parsing).
  `email` API requires email knowledge and maintaining a facade makes things
  harder.
* Merge of the `lettre_email` crate into `lettre`, and more features to allow disabling most features.
* Add the option to use `rustls` for TLS, and use it by default.
* Improved parsing of server responses.
* Moved CI from Travis to Github actions.
* Async support (based on `async-std`).

### Migration from 0.9

TODO

## Road to 1.0

Lettre is now used by several projects, including crates.io itself!
It will be good to have a stable basis for the future.

The plan is that 0.10 is the release preparing the 1.0 in the following months.
I'd also want to add more real-world automated testing with actual mail servers (at least postfix).

## After

* reuse `smtp` crate for the protocol (a bit like `http`)

If you want to contribute, the `lettre` repo and organizations are definitely open for anything
related to email.

Depending on the ecosystem evolution, the future may bring an independent SMTP implementation
(similar to the `http` crate), and a more powerful message representation.
