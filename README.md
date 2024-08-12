# remove_dir_all_ext

[![Latest Version](https://img.shields.io/crates/v/remove_dir_all_ext.svg)](https://crates.io/crates/remove_dir_all_ext)
[![Docs](https://docs.rs/remove_dir_all_ext/badge.svg)](https://docs.rs/remove_dir_all_ext)
[![License](https://img.shields.io/crates/l/remove_dir_all_ext.svg)](https://github.com/gussy/remove_dir_all_ext)

> [!NOTE]
> This is a fork of [remove_dir_all](https://github.com/caesay/remove_dir_all), renamed as `remove_dir_all_ext` for publishing to crates.io

## Description

Reliable and fast directory removal functions.

* `remove_dir_all` - on non-Windows this is a re-export of
  `std::fs::remove_dir_all`. For Windows an implementation that handles the
  locking of directories that occurs when deleting directory trees rapidly.

* `remove_dir_contents` - as for `remove_dir_all` but does not delete the
  supplied root directory.

* `ensure_empty_dir` - as for `remove_dir_contents` but will create the
  directory if it does not exist.

### Extended functions

* `remove_dir_containing_current_executable` - as for `remove_dir_contents` but will delete the directory containing the current executable, leaving only the executable itself.

* `remove_dir_but_not_self` as for `remove_dir_contents` but does not delete the currently running executable.

### Example

```rust,no_run
extern crate remove_dir_all;

use remove_dir_all::*;

fn main() {
    remove_dir_all("./temp/").unwrap();
    remove_dir_contents("./cache/").unwrap();
}
```

## Minimum Rust Version

The minimum rust version for `remove_dir_all` is the latest stable release, and the minimum version may be bumped through patch releases. You can pin to a specific version by setting by add `=` to your version (e.g. `=0.6.0`), or committing a `Cargo.lock` file to your project.
