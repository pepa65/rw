[![version](https://img.shields.io/crates/v/rwh.svg)](https://crates.io/crates/rwh)
[![build](https://github.com/pepa65/rwh/actions/workflows/push.yml/badge.svg)](https://github.com/pepa65/rwh/actions/workflows/push.yml)
[![dependencies](https://deps.rs/repo/github/pepa65/rwh/status.svg)](https://deps.rs/repo/github/pepa65/rwh)
[![docs](https://img.shields.io/badge/docs-rwh-blue.svg)](https://docs.rs/crate/rwh/latest)
[![license](https://img.shields.io/badge/License-EUPLv1.2-blue.svg)](https://github.com/pepa65/rwh/blob/main/LICENSE)
[![downloads](https://img.shields.io/crates/d/rwh.svg)](https://crates.io/crates/rwh)

# rwh 0.13.5
**Rusty Wormhole - Safe filetransfer through magic-wormhole**

* See <http://magic-wormhole.io/>
* Rust port of the Python version: <https://github.com/magic-wormhole/magic-wormhole>
* After: <https://github.com/magic-wormhole/magic-wormhole.rs>
  - Has many unfixed code warnings and security advisories.
* Repo: <https://github.com/pepa65/rwh>
  - This repo fixes all the code warnings and security audit issues of the parent repo above.
* License: EUPL v1.2 or later

## Install
### Install standalone single-binary
```
wget https://github.com/pepa65/rwh/releases/download/0.13.5/rwh
sudo chown root:root rwh
sudo chmod +x
sudo mv qr /usr/local/bin/
```

### Install with cargo
If not installed yet, install a **Rust toolchain**, see https://www.rust-lang.org/tools/install

#### Direct from crates.io
`cargo install rwh`

#### Direct from repo
`cargo install --git https://github.com/pepa65/rwh`

#### Static build (avoiding GLIBC incompatibilities)
```
git clone https://github.com/pepa65/rwh
cd rwh
rustup target add x86_64-unknown-linux-musl
cargo rel  # Alias in .cargo/config.toml
```

The binaries will be in `target/x86_64-unknown-linux-musl/release/`

### Install with cargo-binstall
Even without a full Rust toolchain, rust binaries can be installed with the static binary `cargo-binstall`:

```
# Install cargo-binstall for Linux x86_64
# (Other versions are available at https://crates.io/crates/cargo-binstall)
wget github.com/cargo-bins/cargo-binstall/releases/latest/download/cargo-binstall-x86_64-unknown-linux-musl.tgz
tar xf cargo-binstall-x86_64-unknown-linux-musl.tgz
sudo chown root:root cargo-binstall
sudo mv cargo-binstall /usr/local/bin/
```

Install the binaries for linux-x86_64 (musl): `cargo-binstall eqr`

The binaries will be installed into `~/.cargo/bin/` which still needs to be added to `PATH`!

## Usage
```
rwh 0.13.5 - Safe filetransfer through magic-wormhole
Usage: rwh [OPTIONS] <COMMAND>
Commands:
  send       Send a file/folder [alias: s]
  receive    Receive a file/folder [alias: r]
  send-many  Send a file to many recipients
  forward    Forward ports from one machine to another

Options:
  -v, --verbose   Enable logging to stdout, for debugging purposes
      --no-color  Disable color output
  -h, --help      Print help
  -V, --version   Print version

Run a subcommand with `--help` to know how it's used.
```

## Miscellaneous Information
### Comparison with the Python implementation
Features that are missing:
* Text message sending
* Folder sending (we can send folders, but it will send a tar ball which the other side will have to manually unpack)
* Tor support

New features that exceed the other implementations:
* Can do direct connections across the internet (NATs) and firewalls
* Automatically copies your code to the clipboard
* Port forwarding in addition to file transfer (experimental)
* Send a file to multiple people (experimental)
* Fuzzy wormhole code completion

### Developing
If you want to toy with the CLI, `cargo run -- --help` will get you started. The code sits in `./cli/src`. For more instructions see [cli/README.md](cli/README.md).

If you'd like to use Wormhole in your application, `cargo doc --open` will tell you how to use it. There aren't any hosted docs at the moment.

If you don't fear touching code and want to contribute, `./src/lib.rs`, `./src/transfer.rs` and `./src/transit.rs` are rather easy to get into. The [protocol specification](https://github.com/magic-wormhole/magic-wormhole-protocols) will probably be useful to you.

### Applications using Wormhole Rust as library
* [Warp](https://gitlab.gnome.org/World/warp), a GUI client using Gtk
* [Wormhole File Transfer](https://github.com/wormhole-app/wormhole), a Android client using Flutter
* [Wyrmhole](https://github.com/ClaytonWas/wyrmhole), a cross-platform GUI using Tauri
* [rvIRC](https://github.com/KaraZajac/rvIRC), a vim-based IRC client with filesharing
* Feel free to add yours!

### License
This work is licensed under the EUPL v1.2 or later. Contact the owner(s) for use in proprietary software.

