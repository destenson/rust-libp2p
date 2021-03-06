# [WIP] Central repository for work on libp2p

This repository is the central place for rust development of the
[libp2p](https://libp2p.io) spec.

This readme along with many others will be more fleshed out the closer
the project gets to completion. Right now everything including the crate
organization is very much Work in Progress.

## General overview of the architecture

Architecture of the crates of this repository:

- `datastore`: Utility library whose API provides a key-value storage with multiple possible
  backends. Used by `peerstore`.
- `example`: Example usages of this library.
- `libp2p-peerstore`: Generic storage for information about remote peers (their multiaddresses and
  their public key), with multiple possible backends. Each multiaddress also has a time-to-live.
  Used by `libp2p-swarm`.
- `libp2p-ping`: Implementation of the `ping` protocol (the exact protocol is specific to libp2p).
  Implements the `ConnectionUpgrade` trait of `libp2p-swarm`.
- `libp2p-secio`: Implementation of the `secio` protocol. Encrypts communications. Implements the
  `ConnectionUpgrade` trait of `libp2p-swarm`.
- `libp2p-swarm`: Core library that contains all the traits of *libp2p* and plugs things together.
- `libp2p-tcp-transport`: Implementation of the `Transport` trait of `libp2p-swarm` for TCP/IP.
- `multistream-select`: Implementation of the `multistream-select` protocol, which is used to
  negotiate a protocol over a newly-established connection with a peer, or after a connection
  upgrade.
- `rw-stream-sink`: Utility library that makes it possible to wrap around a tokio `Stream + Sink`
  of bytes and implements `AsyncRead + AsyncWrite`.
