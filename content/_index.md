lettre is an email client for Rust programs allowing easily sending emails from Rust
applications by providing:

* several email transports
* a strongly typed email builder with MIME support (attachments, image embedding)
* internationalized email support
* secure defaults
* low level entry point for custom smtp clients

lettre focuses on modern email client needs and does not intend to extensively implement
email standards.

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
