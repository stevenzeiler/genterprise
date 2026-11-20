# genterprise

A small StrongLoop LoopBack 2 app (npm package `gatewayd4`) that sketches an enterprise-style rewrite of gatewayd, the Ripple gateway server.

> **Status: dormant since October 2014.** Two commits, 2014-10-21 to 2014-10-28, written during Steven's 2014 Ripple gateway era. It was an experiment and was not taken further. I have not run it on a current toolchain.

## What is in it

- A stock LoopBack 2 scaffold: `server/` (boot scripts, config, datasources), `common/models/`, `client/` (an empty placeholder).
- Two models, `ripple_address` (account, optional tag, type) and `ripple_payments` (source and destination address ids, amounts, currencies, issuers, state), both exposed over REST.
- One hand-written boot script, `server/boot/gatewayd-basic-api.js`, that mounts `GET /payments/incoming`.
- Data lives in LoopBack's in-memory connector (`server/datasources.json`), so nothing is saved between runs.

## Install and run

These are the steps the scaffold implies. They are untested here, and LoopBack 2 targets Node versions from that era, so expect trouble on a modern Node.

```sh
npm install
node server/server.js
```

The server listens on port 3000 and the REST API root is `/api` (see `server/config.json`). If `loopback-explorer` installs, the API explorer is at `/explorer`.

## Configuration

There are no environment variables. Host, port and API root are set in `server/config.json`, and the data source in `server/datasources.json`.

## How it works

`server/server.js` creates a LoopBack app and runs `loopback-boot`, which executes everything in `server/boot/` (authentication, explorer, REST API, root status route, and the gatewayd route). Models are loaded from `common/models/` as listed in `server/model-config.json`.

The commit message "Attach gatewayd apis on boot" is more ambitious than the code. The boot script only defines a single route, and it refers to a `server` variable it never receives, so that route would fail when called **(inference, from reading the code)**. It does not load gatewayd itself.

## Status

See [docs/STATUS.md](docs/STATUS.md). Agents should read [AGENTS.md](AGENTS.md).

## License

No license is declared in this repository. See STATUS for the open decision.
