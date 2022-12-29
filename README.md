# Maruko

## $json

```javascript
const data = await $json("filename");
const data = await $json("folder/filename");
```

## $key

```javascript
await $key.set("pg_uri", "postgres://user:password@localhost:5432/postgres");
const uri = await $key("pg_uri");
```

## $mongo

```javascript
const doc = await $mongo("db_name", "collection_name", {
  cmd: "findOne",
  args: [{ title: "xxx" }, ...]
});
```

## $mysql

```javascript
const rows = await $mysql("db_name", "select * from table_name limit 20");
```

## $node

```javascript
const run = useCallback(async () => {
  const result = await $node("return 6 * 7;");
}, []);

const run = useCallback(async () => {
  const result = await $node("return a * a;", { a: 9 });
}, []);

const run = useCallback(async () => {
  const result = await $node(`
    const { networkInterfaces } = require("os");
    const nets = networkInterfaces();
    return nets.en0;
  `);
}, []);
```

## $pg

```javascript
const rows = await $pg("db_name", "select * from table_name");
```

## $py / $pip

```javascript
const run = useCallback(async () => {
  const result = await $py("3 * 7");
}, []);

const run = useCallback(async () => {
  const result = await $py(
    `
    strs = ["*" for x in range(size)]
    strs
  `,
    { size: 8 }
  );
}, []);

const run = useCallback(async () => {
  await $pip("numpy");
  const result = await $py(`
    import numpy as np
    x = np.arange(15, dtype=np.int32).reshape(3, 5)
    x[1:, ::2] = -99
    x
  `);
}, []);
```

## $useState (Hooks) / $setState

```javascript
function MyApp() {
  const count = $useState("count", 0);
  return (
    <View>
      <Text>{count}</Text>
      <Button
        title="Increment"
        onPress={() => {
          $setState({ count: count + 1 });
        }}
      />
    </View>
  );
}
```

## $sql

```javascript
const rows = await $sql("db_name", "select * from table_name");
```

## $var (Node.js) / $useVar (Hooks)

```javascript
// Node.js
$var.person = {
  name: "dx",
  age: 16,
};

// React Native
function MyApp() {
  const man = $useVar("person");
  return (
    <View>
      <Text>{man.name}</Text>
    </View>
  );
}
```
