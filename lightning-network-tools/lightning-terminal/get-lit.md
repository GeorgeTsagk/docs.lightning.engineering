---
description: >-
  You can install litd on your Linux, MacOS or Windows machine, either in
  integrated or remote mode.
---

# 🛠 Get litd

You can install `litd` from source or via the provided binary. If you are running LND as part of a software bundle like Umbrel, `litd` might already be installed on your node.

[In this case, continue here: Connect to Terminal](run-litd.md)

## Install the binary

Choose this option for a quick and convenient installation. You can find the binaries and verification instructions for the latest release on [Github](https://github.com/lightninglabs/lightning-terminal/releases/).

Once you have downloaded the binary for your operating system, verify them and unpack them, either with your file manager or the command line. This may look like this:

`tar -xvf lightning-terminal-<latest release>-alpha.tar.gz`

Or on Windows:

`tar -xvzf C:\path\lightning-temrinal<latest-release>-alpha.tar.gz -C C:\path\litd`

You can now execute the program from its location, or place it where the system can conveniently find it, such as `/bin/litd` on Linux.

[Continue here: Connect to Terminal](run-litd.md)

## Install from source

### Prerequisites <a href="#docs-internal-guid-7cbeda7b-7fff-ea25-6c45-b336fa1d808e" id="docs-internal-guid-7cbeda7b-7fff-ea25-6c45-b336fa1d808e"></a>

1. You will need Go. If you compiled LND from source this should already be installed on your system. You can find [detailed instructions here](https://golang.org/doc/install).
2. You will need nodejs. You can [download and install it here](https://nodejs.org/en/download/).
3. You will need yarn. You can [download it here](https://classic.yarnpkg.com/en/docs/install). Most conveniently, you can install it with `npm install --global yarn`
4. You will need to run the latest release of LND at least (`lnd v0.14.1`). Have a look at this [upgrade guide](../lnd/run-lnd.md#upgrading-from-source).

To run litd, you must either run the [lnd binaries](https://github.com/lightningnetwork/lnd/releases) or compile it from source with a minimum set of tags:

`make install tags="autopilotrpc chainrpc invoicesrpc routerrpc signrpc walletrpc watchtowerrpc wtclientrpc"`

### Install litd <a href="#docs-internal-guid-ae172929-7fff-f9d0-7921-e6f8acc92f53" id="docs-internal-guid-ae172929-7fff-f9d0-7921-e6f8acc92f53"></a>

1. First we will download the source code from Github

`git clone https://github.com/lightninglabs/lightning-terminal.git`

`git checkout <latest release>`

2\. Now we will install it:

`make install`

The binaries should be found in your Go path, most commonly `~/go/bin/` You can navigate and check your Go path with `cd $GOPATH`

3\. `litd` bundles `poold`, `loopd` and `faraday`. Installing `litd` as above will install the [litcli command line interface](command-line-interface.md), but not pool, loop and frcli, as these might already exist on your sytem. If they do not exist and you wish to install them, you may run the below in addition:

`make go-install-cli`

[Continue here: Connect to Terminal](run-litd.md)

### Install in BTCPay Server

BTCPay contains an installation script for `litd`, which makes it easy to include litd into your BTCPay Server. You may also refer to [the official guide](https://docs.btcpayserver.org/Docker/lightning-terminal/#lightning-terminal-lit).

1. Set a password for your litd instance:

`export LIT_PASSWD="YOUR PASSWORD HERE"`

2\. Add the fragment to your configuration and run the installation script:

`BTCPAYGEN_ADDITIONAL_FRAGMENTS="$BTCPAYGEN_ADDITIONAL_FRAGMENTS;opt-add-lightning-terminal"`\
`. btcpay-setup.sh -i`

You can now find `litd` under Server Settings > Services

[Continue here: Connect to Terminal](run-litd.md)

## Run the litd binary

To run `litd`, you will need to specify a password of your own, ideally using a password manager:

`litd --uipassword=dontusethisyouwillgethacked`

[Continue here: Connect to Terminal](run-litd.md)

