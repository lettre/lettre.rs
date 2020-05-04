---
title: "are we email yet?"
description: "State of Rust email ecosystem"
date: "2020-02-01"
draft: true
---

Email is an old protocol, and has kind of a special place.

It old and patchy, build from 40 years of RFCs and extensions.

Email is old, not loved, but still necessary.

HTTP ecosystem

short email landscape in rust

* [rust-async](https://github.com/async-email/async-smtp), provides a async SMTP transport
  compatible with lettre 0.9 messages.
* [Proposal for a mail WG](https://internals.rust-lang.org/t/starting-a-rust-mail-wg/11678)
* samotop
* mail (and other by 1aim), including async smtp implementation (with tokio 0.1). Not maintained
  anymore, pretty complete.

