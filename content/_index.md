lettre tries to make sending emails from Rust program as safe and
easy as possible. It provides pluggable transports, an email builder
with MIME support (UTF-8 support, attachments, image embedding).

Email is a core part of our legacy, and despite its (numerous) flaws, it stays
our only really interoperable messaging system.

lettre *does not* target exhaustive email RFC implementation, but focuses on the
client only. This may change depending on the Rust email ecosystem and
on external contributions.

* email builder with MIME support (attachments, image embedding)
* easy to use (without deep knowledge about email)
* RFC compliance
* Internationalization
* secure (secure defaults, TLS support)

```rust
use lettre::{Message, SmtpTransport};

let email = Message::builder()
    .from("NoBody <nobody@domain.tld>".parse().unwrap())
    .reply_to("Yuin <yuin@domain.tld>".parse().unwrap())
    .to("Hei <hei@domain.tld>".parse().unwrap())
    .subject("Happy new year")
    .body("Be happy!")
    .unwrap();

// Open a local connection on port 25 and send the email
let mailer = SmtpTransport::unencrypted_localhost();
assert!(mailer.send(&email).is_ok());
```
