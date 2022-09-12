### Variables

```ts
const shade = 100;
type Shade = 100;
```

### Functions

```ts
function hello(msg: string = "Anurag") {
  return `Hello ${msg}`;
}

type Hello<Msg extends string = "Anurag"> = `Hello ${Msg}`;
```

### Arrays or Lists

```ts
const colors = ["red", "green", "blue"];
type Colors = ["red", "green", "blue"];
// or unions   "red" | "green" | "blue"
```

### Conditionals

```ts
function isRGB(color: string) {
  return colors.includes(color) ? true : false;
}

type isRGB<Color extends string> = Color extends Colors ? true : false;
```

### Loops or Mapped types

```ts
const shades = colors.map((color) => `${color}.${shade}`);
type Shades = { [Color in Colors]: `${Color}.${Shade}` }[Colors];
```

### Recursion

```ts
// fillArray(10) -> [0, 1, 2, 3, 4, 5, 6, 7, 8, 9]
function fillArray(limit: number, value: Array<number> = []) {
  if (value.length >= limit) return value;
  return fillArray(limit, [...value, value.length]);
}

type FillArray<
  Limit extends number,
  Value extends Array<number> = []
> = Limit extends Value["length"]
  ? Value
  : FillArray<Limit, [...Value, Value["length"]]>;

type Demo = FillArray<10>;
```

### Object.keys

```ts
const obj = {
  name: "anurag",
  age: 20,
};

const keys = Object.keys(obj); // ['name', 'age]
type Keys = keyof typeof obj; // 'name' | 'age
```

### Property access 

```ts
const name = obj["name"]; // 'anurag'
type Name = typeof obj["name"] // 'anurag'
```
