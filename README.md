# Chainweb Mining Client Binaries

The Chainweb Mining Client (CMC) is the middle man between your ASIC and a Kadena node. CMC gets work from a node and submits the solved work (shares / blocks) to a Kadena node.

Official releases of CMC don't have a compiled binary. I have compiled the released code into an executable for Ubuntu and Windows. My goal is to continue to release binaries for the chainweb-mining-client if official releases don't have them. In other words, I will discontinue compiling binaries only if official releases have them for download.

I have tested the compiled binaries in this repository to make sure they work as intended.

If I make any changes to the source code before compiling, I will note that. For example, I compiled a binary that beeps your computer speaker whenever a block is found. The beeping functionality is not present in the official release. I will compile official releases with zero modification and I will compile one with the "beep".

## How to install / use

- Download your preferred binary release from this repo
- Extract the file to a directory/folder -- /mining-client for example
- Start the mining client with the command below.

Be aware that you would need a synced Kadena node to be able to use CMC. Well, you can use it even without a synced node, but it will be useless because you'll be solving blocks that have been mined. Additionally, you would need to whitelist your Kadena k:account / key on the node you plan to mine on / to (read about Kadena Solo Miners Collective below). Remember, CMC is just the middleman (stratum) receiving work from a node and submitting solved work back to the node.

### For Ubuntu and other Debian distros

```./chainweb-mining-client --no-tls --public-key yourPublicKey --stratum-difficulty 45 --node 10.10.100.10:1848 --log-level debug --thread-count 1 --worker stratum --stratum-port 2020```

### For Windows

```chainweb-mining-client.exe --no-tls --public-key yourPublicKey --stratum-difficulty 45 --node 10.10.100.10:1848 --log-level debug --thread-count 1 --worker stratum --stratum-port 2020```

### Additional information

You can issue this command to see available options for CMC

Ubuntu: ```./chainweb-mining-client -h```

Windows: ```chainweb-mining-client.exe -h```

For your mining client to work, it needs to connect to a node. You will need to provide a node that you have authorization to mine on.

```--node 10.10.100.10:1848``` or ```--node --node domainName:1848```

Port 1848 is hardcoded and can't be changed; that's Kadena node service API port.

Difficulty for under 100 combined terahash should be in the range of 45 to 50. If you don't want to submit shares as often, then you can increase the difficulty or just use `block` instead. Using `block` means you'll only send shares that solve a block to CMC -- not advisable unless you have massive amount of hash power.

Thread count should be what you think it should be. If you're connecting under 50 machines, I think 1 thread per 10 KD Boxes is good. If not, experiment.

Stratum port is whatever port you want to use. Just make sure you're not using a port already in use. If that's the case, the program will tell you - read error messages.

### Kadena Solo Mining Collective

This is a collective I started to allow solo miners come together to mine as group. There will be regional hosts for different parts of the world for better latency. Additionally, this is FREE. I will have volunteers who will provide servers that will be mined on. Having a collective of solo miners helps decentralize the Kadena network.

Poolflare is the best pool, hands down. Nothing compares. I still have some of my miners on there but still solo mining at the same time. Since Poolflare controls almost 80% of the network hashrate, it makes sense to spread the hashrate around. Joining this collective might help so that we earn similar, if not more than we would earn mining on Poolflare. If Poolflare had 40% of the hashrate, that won't be an issue, but they have most of the network hashrate.

Happy Mining!

Click [here](https://github.com/kadena-io/chainweb-mining-client) to visit the Official mining client repository.







