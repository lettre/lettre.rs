---
title: "towards lettre 1.0"
description: "towards lettre 1.0"
date: "2020-11-25"
draft: true
---


#### background: a bit of history

The `lettre` crate was previously named [`smtp`](https://crates.io/crates/smtp). It [started](https://github.com/lettre/lettre/commit/270efd193a11e66dce14700a50d3c42c12e725bc) in early 2014 (before cargo, Rust 1.0, etc.).

The first goal was to start a toy project to learn Rust. I started with an `smtp` implementation after seeing there was no existing implementation in Rust. Originally, the project aimed at implementing the `SMTP` protocol for client and server.

In 2016, the goal changed, and specialized to email client (as I did not see much use in another SMTP server may it be written in Rust). The project also moved away from "just SMTP" to email client, and was renamed to lettre at this time. Why `lettre`? After some time looking for a fitting name, not already taken by email-related software, I ended up just taking the the French word for "letter"!
