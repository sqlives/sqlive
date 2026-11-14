# sqlive

Live queries for SQLite: a document store on top of SQLite whose query results stay current as
writes commit. Runs on sqlite-wasm (OPFS) in the browser, on Node, and on React Native.

> Work in progress. Nothing is published yet and the API will change.

## Why

- **Live queries that mostly do not touch the database.** A committed write is applied to each
  live result in memory; SQL runs again only when a row from outside the page has to move in.
- **Rows that did not change keep their object identity**, so memoised UI rows skip rendering.
- **Group commit.** Writes issued while a transaction is in flight share the next one.
- **Real SQLite indexes**, so a sorted, limited list costs the same on a thousand rows or a million.

## Repository

| Path            | What                                            |
| --------------- | ----------------------------------------------- |
| `packages/core` | `sqlive`: database, collections, live queries   |
| `apps/bench`    | Browser playground for measuring storage and UI |

## Development

```bash
pnpm install
pnpm typecheck
pnpm test
```

Needs Node 22.13 or newer (the tests run on `node:sqlite`).

## License

MIT
