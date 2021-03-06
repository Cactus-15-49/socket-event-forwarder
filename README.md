# Socket event forwarder
A plugin for forwarding real-time blockchain events through socket.io.

Supported blockchain events can be found [here.](https://github.com/ArkEcosystem/core/blob/master/packages/core-event-emitter/src/index.ts#L12-L45)

## Custom events

- `transaction.confirmed` fired when a transaction is confirmed for a configurable amount of times. [A demo can be found here.](https://radians.nl/realtime-transaction-confirmation-demo)
- `systeminformation` fires system information like CPU, memory and filesystem stats at an configurable interval.
- `network.latency` fires the stats of a HTTP request to measure latency in milliseconds at an configurable interval.
- `blockheight.current` fires the current synced blockheight at an configurable interval.

## Installation
#### From source

1. clone the plugin with `cd ~/{core-bridgechain}/plugins && git clone https://github.com/e-m-s-y/socket-event-forwarder`
2. add plugin configuration to the bottom of `~/.config/{bridgechain-core}/{mainnet|devnet|testnet}/plugins.js`
3. bootstrap the plugin `cd ~/{core-bridgechain}/plugins && yarn bootstrap`
4. restart your relay / forger process.

#### Yarn
1. `yarn global add @foly/socket-event-forwarder`
2. add plugin configuration to the bottom of `~/.config/{bridgechain-core}/{mainnet|devnet|testnet}/plugins.js`
3. restart your relay / forger process.

#### Example configuration
```js
"@foly/socket-event-forwarder": {
    port: 3333, // The port of the socket server
    events: ["block.applied"],  // Events that you want to forward
    confirmations: [5, 15, 51], // The amount of confirmations needed before firing the transaction.confirmed event 
    customEvents: ["transaction.confirmed", "systeminformation", "network.latency"], // Enabled custom events
    systeminformationInterval: 5000, // Interval of systeminformation event
    networkLatencyInterval: 10000, // Interval of network.latency event
    blockheightCurrentInterval: 10000 // Interval of blockheight.current event
}
```
## Credits

- [e-m-s-y](https://github.com/e-m-s-y)

## License

[MIT](LICENSE)
