
# GENERAL RUNDOWN
Compiling Rust code to WebAssembly (Wasm) is a common task for creating high-performance web applications. Here's a step-by-step guide to compile Rust code to Wasm:

 1. **Install the wasm32-unknown-unknown target**: Rust needs to be able to compile to the WebAssembly target. You can install it using Rustup by running:
   ```
   rustup target add wasm32-unknown-unknown
   ```

2. **Write your Rust code**: Create your Rust code file, for example, `lib.rs`.

3. **Add dependencies**: If your Rust code uses external dependencies, ensure they are specified in your `Cargo.toml` file.

4. **Configure Cargo for Wasm**: Add the following section to your `Cargo.toml` file to configure Cargo for building Wasm:
   ``` toml
   [lib]
   crate-type = ["cdylib"]
   ```

6. **Build the Wasm file**: Run the following command to build your Rust code into a Wasm file:
   ```
   cargo build --target wasm32-unknown-unknown
   ```

7. **Use the Wasm file**: After building, you'll find the Wasm file in the `target/wasm32-unknown-unknown/debug` directory (or `target/wasm32-unknown-unknown/release` if you built with `--release` flag). This Wasm file can be used in your web application.

8. **Integration with JavaScript**: To interact with the Wasm module from JavaScript, you'll need to write some glue code. You can use tools like `wasm-bindgen` to generate JavaScript bindings automatically, simplifying the integration process.

Here's a basic example of how you might interact with your Rust-generated Wasm module from JavaScript:

```javascript
fetch('your_module.wasm')
  .then(response => response.arrayBuffer())
  .then(bytes => WebAssembly.instantiate(bytes, {}))
  .then(obj => {
    const { exports } = obj.instance;
    // Use exports provided by your Rust code here
  });
```

That's it! You've now compiled your Rust code to WebAssembly. Remember to handle errors appropriately and consider optimizations for performance-critical code.


# WRITE A LIB 
Sure, here's a simple example of a `lib.rs` file that defines a function to add two numbers together:

```rust
// Define a function to add two numbers
#[no_mangle] // Ensure that the function name is not mangled
pub extern "C" fn add(a: i32, b: i32) -> i32 {
    a + b
}
```

In this example:

- `#[no_mangle]` ensures that the function name is not mangled during compilation, which makes it easier to call from other languages like JavaScript.
- `pub extern "C"` declares a public function that can be called from outside the Rust module and specifies the ABI (Application Binary Interface) as C, which ensures compatibility with WebAssembly.

You can use this function in your Rust code, and when compiled to WebAssembly, it will be callable from JavaScript.


# CREATE CARGO LIB
To create a new Rust project using Cargo, you can follow these steps:

1. **Create a new project**: Open your terminal or command prompt, navigate to the directory where you want to create your project, and run the following command:

   ```
   cargo new my_wasm_project --lib
   ```

   This command creates a new Rust project named `my_wasm_project` with a library crate.

2. **Navigate into the project directory**: Go into the directory of your newly created project:

   ```
   cd my_wasm_project
   ```

3. **Write your Rust code**: Open the `src/lib.rs` file in your favorite text editor and write your Rust code. For example, you can use the code snippet I provided earlier to define a function to add two numbers.

4. **Configure Cargo for Wasm**: Modify the `Cargo.toml` file to configure Cargo for building WebAssembly. Add the following section:

   ```toml
   [lib]
   crate-type = ["cdylib"]
   ```

   This tells Cargo to build the Rust code as a dynamic library suitable for linking with other languages, like JavaScript.

5. **Build the Wasm file**: Run the following command to build your Rust code into a WebAssembly file:

   ```
   cargo build --target wasm32-unknown-unknown
   ```

   This command compiles your Rust code to WebAssembly, targeting the WebAssembly platform.

6. **Use the Wasm file**: After building, you'll find the WebAssembly file in the `target/wasm32-unknown-unknown/debug` directory (or `target/wasm32-unknown-unknown/release` if you built with `--release` flag). This file can be used in your web application.

That's it! You've now created a Rust project and compiled it to WebAssembly using Cargo. You can continue to develop your Rust code and build it as needed for your web application.

# JAVASCRIPT TO TEST
Certainly! Below is a basic HTML file along with JavaScript code that loads and interacts with the WebAssembly file generated from Rust:

**index.html:**

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>WebAssembly Test</title>
</head>
<body>
    <h1>WebAssembly Test</h1>
    <p>Result of adding 5 and 7: <span id="result"></span></p>

    <script>
        // Load the WebAssembly module
        fetch('my_wasm_project.wasm')
            .then(response => response.arrayBuffer())
            .then(bytes => WebAssembly.instantiate(bytes, {}))
            .then(obj => {
                const { instance } = obj;
                const { add } = instance.exports;

                // Call the add function from Rust
                const result = add(5, 7);

                // Display the result on the HTML page
                document.getElementById('result').textContent = result;
            })
            .catch(err => {
                console.error('Error loading WebAssembly module:', err);
            });
    </script>
</body>
</html>
```

This HTML file loads the WebAssembly module (`my_wasm_project.wasm`), instantiates it, and then calls the `add` function exported from the module with arguments 5 and 7. It displays the result on the webpage.

Ensure that you replace `'my_wasm_project.wasm'` with the correct path to your compiled WebAssembly file.

You can serve this HTML file and your WebAssembly file using a local development server or by simply opening the HTML file in your browser.