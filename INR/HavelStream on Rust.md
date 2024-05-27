TO DO :
1. find a way to load weights into a rust library to do a feedfarward
2. model an API for  javascript to execute the code from the rust library 
3. display an image from the methods of the api and print it on the screen from the javascript

One popular Rust library for creating neural network models is `tch-rs`, which is a Rust binding for the PyTorch deep learning framework. PyTorch is widely used for building neural network models in Python, and `tch-rs` allows you to leverage the power of PyTorch directly within Rust code.

Here's a basic example of how you might use `tch-rs` to create a simple neural network:

```rust
use tch::{nn, nn::OptimizerConfig, nn::Module, nn::ModuleT, nn::Optimizer};

struct SimpleNet {
    layer1: nn::Linear,
    layer2: nn::Linear,
}

impl SimpleNet {
    fn new(vs: &nn::Path) -> SimpleNet {
        let layer1 = nn::linear(vs, 784, 100, Default::default());
        let layer2 = nn::linear(vs, 100, 10, Default::default());
        SimpleNet { layer1, layer2 }
    }
}

impl nn::Module for SimpleNet {
    fn forward(&self, xs: &tch::Tensor) -> tch::Tensor {
        xs.view([-1, 784])
            .apply(&self.layer1)
            .relu()
            .apply(&self.layer2)
    }
}

fn main() {
    let vs = nn::VarStore::new(tch::Device::cuda_if_available());
    let net = SimpleNet::new(&vs.root());
    let mut opt = nn::Adam::default().build(&vs, 1e-3).unwrap();

    // Training loop...
}
```

In this example, we define a simple neural network with two linear layers using `tch-rs`. We create a struct `SimpleNet` with two linear layers, and implement the `nn::Module` trait for it, specifying how the forward pass should be computed. Then, in the `main` function, we create an instance of the network, initialize an optimizer, and set up the training loop.

`Tch-rs` provides a Rust-friendly interface for working with neural networks, making it a good choice for building deep learning models in Rust.


The `tch-rs` library provides bindings to the PyTorch library, which is primarily implemented in C++. PyTorch itself is highly optimized for performance, leveraging CUDA for GPU acceleration where available, and providing efficient CPU implementations as well.

While Python is often criticized for its performance compared to lower-level languages like C++ or Rust, the performance of PyTorch models executed through `tch-rs` in Rust should be comparable to running them in Python. Rust itself is known for its performance and memory safety features, so using `tch-rs` to build and execute neural network models can offer the benefits of both the high-level abstractions and ease of use of PyTorch, as well as the performance and safety features of Rust. 

However, it's worth noting that the performance of your application will depend on various factors including the complexity of your neural network, the size of your dataset, and how efficiently you write your Rust code. As with any performance-critical application, it's important to profile and optimize where necessary.