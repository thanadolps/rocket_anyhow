# rocket_anyhow

This library provided `rocket_anyhow::Error`,
a wrapper around [anyhow::Error]
with rocket's [responder] implemented.

[anyhow::Error]: https://docs.rs/anyhow/1.0/anyhow/struct.Error.html
[responder]: https://api.rocket.rs/v0.5-rc/rocket/response/trait.Responder.html

```rust
use std::io::Write;

#[post("/<path..>", data="<text>")]
fn write_utf8_to(path: std::path::PathBuf, text: Vec<u8>) -> rocket_anyhow::Result {
   let mut file = std::fs::File::open(path)?;
   let text = std::str::from_utf8(&text)?;
   file.write_all(text.as_ref())?;
   Ok(())
}

```
