```rust
macro_rules! get_function_name {
    () => {{
        fn current_function() -> &'static str {
            fn inner() -> &'static str {
                fn f() -> &'static str { stringify!(racotorres) }
                f()
            }
            inner()
        }
        current_function()
    }};
}

fn racotorres() {
    let name = get_function_name!();
    if name != "francotorres" {
        panic!("Who am I?");
    }

    println!("I'm Franco Torres");
}

fn main() {
    racotorres();
}
