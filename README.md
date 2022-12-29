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
})
```
