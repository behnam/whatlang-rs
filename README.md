# Whatlang

[![Build Status](https://travis-ci.org/greyblake/whatlang-rs.svg?branch=master)](https://travis-ci.org/greyblake/whatlang-rs)

Natural language detection for Rust. [Documentation](https://docs.rs/whatlang).

## Features
* Supports [84 languages](https://github.com/greyblake/whatlang-rs/blob/master/SUPPORTED_LANGUAGES.md)
* 100% written in Rust
* No external dependencies
* Fast
* Recognizes not only a language, but also a script (Latin, Cyrillic, etc)

## Get started

Add to you `Cargo.toml`:
```
[dependencies]

whatlang = "0.3.1"
```

Small example:

```rust
use whatlang::{detect, Lang, Script};

// Detect Esperanto (there are also `detect_lang` and `detect_script` functions)
let info = detect("Ĉu vi ne volas eklerni Esperanton? Bonvolu!").unwrap();
assert_eq!(info.lang, Lang::Epo);
assert_eq!(info.script, Script::Latin);
```

## Blacklisting and whitelisting

You can create configured detector to apply blacklist or whitelist:

```rust
use whatlang::{Detector, Lang};

const WHITELIST : &'static [Lang] = &[Lang::Eng, Lang::Rus];

// You can also create detector using `with_blacklist` function
let detector = Detector::with_whitelist(WHITELIST);

// There are also `detect` and `detect_script` functions
let lang = detector.detect_lang("There is no reason not to learn Esperanto.");
assert_eq!(lang, Some(Lang::Eng));
```

For more details, please check [documentation](https://docs.rs/whatlang/).

## Running benchmarks

```
cargo bench
```

## Roadmap

* ~~Support about 100 languages (actually at the moment it's 84)~~
* ~~Allow to specify blacklist for Query~~
* ~~Allow to specify whitelist for Query~~
* ~~[Support new API](https://github.com/greyblake/whatlang-rs/issues/5)~~
* ~~Write doc for public structures and functions~~
* ~~Improve README example~~
* ~~Implement benchmarks~~
* ~~Tune performance~~
* ~~Create examples~~
* Provide some metrics about reliability(confidence) in `Info` struct

## License

MIT

## Acknowledgments

* Thanks [Franc JS](https://github.com/wooorm/franc) for trigrams dataset.

## Contributors

- [greyblake](https://github.com/greyblake) Potapov Sergey - creator, maintainer.
- [Dr-Emann](https://github.com/Dr-Emann) Zachary Dremann - optimization and improvements
