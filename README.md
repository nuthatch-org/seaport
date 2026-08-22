# seaport

A [nuthatch](https://github.com/nightswatchhq/nuthatch) nest: **Seaport 1.6 on Ethereum**.

OpenSea's settlement layer: order fulfilment, cancellation and counter changes.

One binary, one config file, no graph-node, no gateway, no query fees.

## What it indexes

**Chain:** `mainnet`. **1 contract**, **5 tables**.

| alias | address |
|---|---|
| `c0` | `0x0000000000000068f116a894984e2db1123eb395` |

## Verified

Indexed blocks **25,791,621 to 25,811,557** and sealed **42,123 events**. Every table below is generated from the vendored ABIs, and the run above is what this nest actually decoded, not an estimate.

## Run it

```sh
nuthatch init --from https://github.com/nightswatchhq/seaport
cd seaport
nuthatch dev --dir . --backfill 50000 --seal-direct
nuthatch sql --dir . "SELECT count(*) FROM \"c0__counter_incremented\""
```

The endpoint in `nuthatch.toml` is keyless and public, so this file is publishable: a `nuthatch.toml` is pinned into the nest's content address and must never carry a credential. It is enough to follow the tip. A **backfill** wants archive depth it may not have: pass your own with `--rpc`, and check it first with `nuthatch doctor --rpc <url>`.

## Tables

```
c0__counter_incremented
c0__order_cancelled
c0__order_fulfilled
c0__order_validated
c0__orders_matched
```
