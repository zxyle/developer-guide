```rust
fn main() {
    // 1. Hello world程序
    println!("Hello, world!");

    // 变量默认不可变 (可变需要加上mut)
    let mut x = 5;
    println!("The value of x is: {}", x);
    x = 6;
    println!("The value of x is: {}", x);


    let spaces = "   ";
    let spaces = spaces.len();
    println!("The value of spaces is: {}", spaces);


    let guess: u32 = "42".parse().expect("Not a number!");
    println!("{}", guess);

    // let age: i64 = 100;

    let tup: (i32, f64, u8) = (500, 6.4, 1);
    println!("{:?}", tup);

    let number = 3;

    if number < 5 {
        println!("condition was true");
    } else {
        println!("condition was false");
    }
}
```

