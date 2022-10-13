# @individe/libp2p-snappy-muxer <!-- omit in toc -->

[![individe.xyz](https://img.shields.io/badge/project-individe-black.svg?style=flat-square)](https://individe.xyz/)

> libp2p's mplex muxer extended with snappy compression, made to be used with Individe IPFS nodes.

## Table of contents

- [Install](#install)
- [Usage](#usage)
  - [`libp2p`](#libp2p)
  - [`ipfs`](#ipfs)
- [License](#license)

## Install

```console
$ npm i @individe/libp2p-snappy-muxer
```

[![](https://github.com/libp2p/interface-stream-muxer/raw/master/img/badge.png)](https://github.com/libp2p/interface-stream-muxer)

## Usage

Snappy muxer extends Mplex. It compresses all outgoing streams towards nodes that implement **/mplex/snappy/x.x.x** multistream protocol and decompresses incoming streams from the nodes that implement that same protocol. Compression algorithm used is snappy.

### libp2p

```js
import { SnappyMplex } from '@individe/libp2p-snappy-muxer'
import { createLibp2p } from 'libp2p'

const node = await createLibp2p({
  streamMuxers: [
    new SnappyMplex()
  ]
})
```

### ipfs

```js
import { SnappyMplex } from '@individe/libp2p-snappy-muxer'
import { createLibp2p } from 'libp2p'
import * as IPFS from 'ipfs-core'

(async () => {
  const libp2p = await createLibp2p({
    streamMuxers: [
      new SnappyMplex()
    ]
  })

  const ipfs = await IPFS.create({
    libp2p: libp2p
  })
})()
```

## License

Licensed under either of

- Apache 2.0, ([LICENSE-APACHE](LICENSE-APACHE) / <http://www.apache.org/licenses/LICENSE-2.0>)
- MIT ([LICENSE-MIT](LICENSE-MIT) / <http://opensource.org/licenses/MIT>)