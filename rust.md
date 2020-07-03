This is an incomplete, always in progress collection of questions about Rust.

- Why does a recursive type need indirection?

- Why does a scope exit not dropped an exclusive reference?
  ```rust
  struct Bop;
  struct Foo;

  struct Bar<'a> {
      objs: Vec<&'a Foo>,
  }

  impl<'a> Bar<'a> {
      fn call(&mut self, _: Bop) {}
  }

  struct Baz<'a> {
      bar: &'a mut Bar<'a>,
  }

  impl<'a> Baz<'a> {
      fn new(bar: &'a mut Bar<'a>) -> Self {
	  Baz { bar }
      }

      fn call(&mut self, _: &'a Bop) {}
  }

  fn run<'a>() {
      let bop = Bop {};
      let foo = Foo {};

      let mut bar = Bar { objs: Vec::new() };
      bar.objs.push(&foo);

      {
	  let mut baz = Baz::new(&mut bar);
	  baz.call(&bop);
	  // baz dropped here? reference dropped too?
      }

      // Borrow OK since baz dropped in scope above?
      // error[E0505]: cannot move out of `bop` because it is borrowed
      bar.call(bop);
  }

  fn main() {}
  ```

