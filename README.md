# spacessh

SSH and SSHFS over the [Spaceswarm DHT](https://github.com/samooth/spacedht)!

## Installation
```
npm install -g spacessh // ssh / fuse client stubs
npm install -g spacetele // spaceswarm server proxy
npm install -g space-cmd-utils // keygen utils
```

## Usage

### Server

On a server

```sh
space-cmd-util-keygen --gen_seed
-> SEED

spacetele-server --seed SEED -l 22
-> PEER_KEY
```

This will start announcing the server on the DHT.

### Client

On the client

```sh
spacessh -s ab01f... -u maf
spacessh -s ab01f... -u maf -i keypair.json
```

Read more about using identities here: https://github.com/samooth/space-cmd-docs/blob/main/identity.md

SSHFS (mount a remove fs/folder via ssh)

```sh
spacessh-fuse -s ab01f... -u maf -m ~/mnt
```

Spaceswarm will do UDP holepunching under the hood, so even if your server is located on a home network it should be accessible.

### Windows RDP

You can also use spacessh with Windows RDP to remotely log in to your windows machines.

On the server
```sh
spacetele-server --seed SEED -l 3389
```

On the client
```sh
spacessh --rdp -s ...
```

## The space-cmd system

spacessh supports the space-cmd system!

Identity management: https://github.com/samooth/space-cmd-docs/blob/main/identity.md

Host resolution: https://github.com/samooth/space-cmd-docs/blob/main/resolve.md

## License

MIT
