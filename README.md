# TSS WASM
portable lightweight client application for threshold ECDSA (based on [GG18](https://eprint.iacr.org/2019/114.pdf)), built on&for [multi-party-ecdsa](https://github.com/ZenGo-X/multi-party-ecdsa) : 
1) Wasm
2) HW friendly

# Npm publish

* node: yarn build_node
* web: yarn build

## Latest release

web: @ieigen/tss-wasm@0.0.6

nodejs: @ieigen/tss-wasm-node@0.0.6, node 18.0+ is required

# Test

## Unit Test
```
yarn build
yarn test
```

## Functional Test via NodeJS
```
cargo build --examples --release
./target/release/examples/gg18_sm_manager

# open another console
yarn build_node
node scripts/run_keygen_sign_node.js
```

## Functional Test via Web

```
cargo build --examples --release
./target/release/examples/gg18_sm_manager

# open another console
yarn build
export NODE_OPTIONS=--openssl-legacy-provider
yarn webpack && yarn webpack-dev-server
```

Open `http://localhost:8080/` in browser, check out the output in `console`.

# Compile SM server by Docker

```
docker build -t ieigen:tss-sm-server --build-arg "BUILDARCH=$(uname -m)" -f sm.dockerfile .
docker run -d -p 8000:8000 -v $PWD/params.json:/tss-wasm/params.json ieigen:tss-sm-server
```

# licence
GPL & Apache-2.0
