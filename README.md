This repo is for reproducing a bug in [Juniper][].

Run `cargo test` to reproduce the error:

```
$ cargo test
    Finished dev [unoptimized + debuginfo] target(s) in 0.06s
     Running target/debug/deps/jfs_bug-5c421a48cb7381a1

running 4 tests
test countries ... ok
test users ... ok
test both_in_different_order ... FAILED
test both ... FAILED

failures:

---- both_in_different_order stdout ----
thread 'both_in_different_order' panicked at 'assertion failed: `(left == right)`
  left: `"users"`,
 right: `"countries"`', src/lib.rs:18:9
note: Run with `RUST_BACKTRACE=1` environment variable to display a backtrace.

---- both stdout ----
thread 'both' panicked at 'assertion failed: `(left == right)`
  left: `"countries"`,
 right: `"users"`', src/lib.rs:12:9


failures:
    both
    both_in_different_order

test result: FAILED. 2 passed; 2 failed; 0 ignored; 0 measured; 0 filtered out

error: test failed, to rerun pass '--lib'
```

Tested on `rustc 1.35.0 (3c235d560 2019-05-20)`

[Juniper]: https://github.com/graphql-rust/juniper
