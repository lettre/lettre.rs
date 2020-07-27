lettre makes sending emails from Rust programs as safe and
hard to misuse as possible, without having to know too much about email
internals.

lettre focuses on modern email client needs and does not intend to extensively implement
email standards.

it provides:

* several transports (in addition to smtp)
* a strongly typed email builder with MIME support (attachments, image embedding)
* internationalized email support
* secure defaults
* low level entry point for custom smtp clients

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
