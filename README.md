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
