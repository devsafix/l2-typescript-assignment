# I'm learning TypeScript right now and writing down some of the things that confused me at first but now kinda make sense. This blog is about:

1. What are the differences between **Interfaces** and **Types** in TypeScript?
2. How TypeScript helps in writing better code and keeping projects clean and easy to manage.

---

## 1. Interfaces vs Types in TypeScript

In JavaScript, we don’t usually write out the "shape" of our objects. We just create them and hope they work. But in TypeScript, we can describe how data should look. For that, we use `interface` and `type`.

At first I thought both are same. But actually, they’re not exactly same. Here's what I found:

### Interface

- Use when you want to describe the **shape of an object** (like a blueprint).
- You can **extend** it (like inheritance in classes).
- You can **merge** multiple interfaces with same name.

```ts
interface User {
  name: string;
}

interface User {
  age: number;
}

const user: User = {
  name: "John",
  age: 30,
};
```

I use interface mostly when working with classes or when defining object models.

---

### Type

- `type` can do **more** things than interface.
- You can use it for **union**, **intersection**, **tuples**, etc.
- You can’t merge types with same name.
- Can still describe objects, like interface.

```ts
type Car = {
  brand: string;
};

type ElectricCar = Car & {
  battery: number;
};
```

#### What should I use?

I use interface when it’s just a simple object. But if I need union or combining types or want to do fancy stuff, then I go for `type`.

---

## 2. TypeScript Helps with Code Quality & Maintainability

Before TypeScript, I was doing JavaScript only. It worked but sometimes I didn’t know where my bugs came from bug. After using TS, I started to see errors **before** running the code. That’s a big help.

Here are some ways TS helped me so far:

### Catches Errors Early

You know right away if you mess up a type.

```ts
function double(n: number) {
  return n * 2;
}

double("5"); // Error: Argument of type 'string' is not assignable to parameter of type 'number'
```

In JS this would just return `NaN`, which is super annoying. But TS gives error while writing!

---

### Autocomplete and IntelliSense

When I define types, VS Code shows auto suggestions and what properties exist. It makes coding faster and less guessing.

```ts
type Book = {
  title: string;
  author: string;
};

const myBook: Book = {
  title: "TS for Beginners",
  author: "Me", // editor helps me here!
};
```

---

### Clean & Organized Code

When I work on big project (I tried one with 20+ files), I could see the benefit. Everything was typed, so if I changed one interface, all files that used it showed errors until I fixed them. So no more hidden bugs.

Also when working with teammates, they can easily understand what a function expects and returns.

---

### Example with Interface + Function

```ts
interface Product {
  name: string;
  price: number;
}

function getDiscount(product: Product): number {
  return product.price * 0.1;
}
```

Now anywhere I call `getDiscount`, I must pass a `Product` type, or TS will show error. That means better code and less runtime errors.

---

## Author

**Kawser Ferdous Safi** – [devsafix.vercel.app](https://devsafix.vercel.app)
