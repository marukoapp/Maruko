# Maruko (丸程序) - Write Personal App

## Next App, Do It Yourself.

Maruko lets you write React Native applications on your phone. And with a powerful interface, you can connect to a database, read data, and then render it in React Native. app also provides file management features, a large number of built-in third-party libraries, and offers very powerful programming capabilities.

Maruko also enables you to call Node.js and Python code directly in React Native and render the returned results in React Native. node.js and Python include a large number of libraries that can be used out of the box.

[AppStore](https://apps.apple.com/app/id1638037174)

## Examples

### $useState (Hooks) / $setState

```javascript
// React Native
function MyApp() {
  const count = $useState("count", 0);
  return (
    <View>
      <Text>{count}</Text>
      <Button
        title="Increment"
        onPress={() => {
          // $setState("count", count + 1);
          $setState({ count: count + 1 });
        }}
      />
    </View>
  );
}
```

### $file

```javascript
// React Native & Node.js
const appDocumentsFolder = $file();
const uri = $file("filename.txt");
const uri = $file("folder/filename.png");
```

### $json

```javascript
// React Native & Node.js
const data = await $json("filename"); // or filename.json
const data = await $json("folder/filename");
```

### $sql

```javascript
// React Native
const rows = await $sql("db_name", "select * from table_name");
```

### $pg

```javascript
// React Native
const rows = await $pg("db_name", "select * from table_name");
```

### $mysql

```javascript
// React Native
const rows = await $mysql("db_name", "select * from table_name limit 20");
```

### $mongo

```javascript
// React Native
const doc = await $mongo("db_name", "collection_name", {
  cmd: "findOne",
  args: [{ title: "xxx" }, ...]
});
```

### $node

```javascript
// React Native
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

### $py / $pip

```javascript
// React Native
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

### $var / $useVar

```javascript
// Node.js
$var.person = {
  name: "dx",
  age: 16,
};

// React Native (Hooks)
function MyApp() {
  const man = $useVar("person");
  return (
    <View>
      <Text>{man.name}</Text>
    </View>
  );
}
```

### $alert

```javascript
$alert("message");
$alert({
  title: "title",
  message: "message"
});
```

### $keychain

```javascript
// React Native
await $keychain.set("pg_uri", "postgres://user:password@localhost:5432/postgres");
const uri = await $keychain("pg_uri");
```

### $log

```javascript
// React Native & Node.js
$log("success");
$log("Network", {
  url: "https://xxx.com/upload",
  filename: "foo.pdf",
  success: true
});
$log(new Error("something wrong"));
```

### $app

```javascript
// Access information about the running app.
// React Native & Node.js
$app: {
  id: string,
  color: string,
  path: {
    DOCUMENTS: string
  }
}
```
