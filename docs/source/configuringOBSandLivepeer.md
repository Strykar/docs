This document is a recipe for how to broadcast on Livepeer.

It will explain what equipment you will need to start.

It will also provide a very simple step-by-step method to install and configure the required software.

It may seem long, but it works. I hope. If it doesn't, come and find me at http://gitter.im/chrishobcroft

Equipment
---------

In order to create a broadcaster node using `Livepeer` and `OBS` you will need:

- 1 x laptop / desktop / server + peripherals

  - running `Linux` or Apple Mac (starting from a clean OS install is not required but always preferable)
  
    - binaries are compiled for x86-64, requires MacOS 10.10 or above

  - connected to internet with at least 330kbps upload bandwidth)

  - with power supply

Method
-------

1. Create a streaming node using Livepeer.

1.1 Download livepeer software

1.1.1 Go to `https://github.com/livepeer/go-livepeer/releases

1.1.2 Download the .zip file corresponding to your operating system (Linux, Mac)

1.1.3 Extract the content of the .zip file into your "favourite folder"

1.2 Run livepeer

1.2.1 open a command-line-interface (such as terminal) in your "favourite folder"

1.2.2 run the following command:

```
./livepeer -rinkeby -v 6
```

`-rinkeby` is to connect the software to the Rinkeby Ethereum Testnet
`-v 6` is to output the highest level of logging

1.2.3 create a "Passphrase"

- This is used to lock and unlock your account, so keep it safe
- You will be asked for this every time you start running the node.
- Enter this Passphrase twice to validate

1.2.4 enter the Passphrase

- This unlocks the account

When you see the following message, then the streaming node is running:

```
LPMS Server listening on :1935
```

1.3 configure livepeer

1.3.1 open another command-line-interface in your "favourite folder"

1.3.2 run livepeer_cli:

```
./livepeer_cli
```

- This will display the configuration of the node
- Also, this provides a richer "menu-based" command-line-interface to help you to get started

1.3.3 get test Ethereum

1.3.3.1 copy the "ETH Account" from the NODE STATS to your clipboard.

- This is a hexadecimal string starting with 0x, such as `0x0dDB225031cCB58fF42866f82D907F7766899014`
- *Make a note of this, because you will be using it a lot.*

1.3.3.2 Go to either of www.twitter.com, www.facebook.com or plus.google.com

- Twitter is easiest, if you have an account already.

1.3.3.3 create a new *public* post containing the "ETH Account" in the text of the post

- For example: https://twitter.com/LivepeerTV/status/974727781836820480

1.3.3.4 copy the URL for the post to your clipboard

- For Twitter, select "Copy link to tweet" on the right hand side of the tweet

1.3.3.5 open http://faucet.rinkeby.io in a browser

1.3.3.6 paste the URL for the post into the field, and click "Give me Ether"

- This will transfer some test Ethereum into your "ETH Account"
- This can take up to 10 minutes to arrive, but often happens in seconds, maybe faster

1.3.4 Validate that you have received the Ethereum

1.3.4.1 open https://rinkeby.etherscan.io in a browser

1.3.4.2 paste the ETH Account into the search bar

1.3.4.3 view your balance in the ETH Account.

- There should now be 1 transaction
- If you do not have any Ethereum in your account, contact the Livepeer Team at http://gitter.im/livepeer and someone there will be happy to help you get some test Ethereum.

1.3.5 get test LPT

1.3.5.1 go to the terminal window where livepeer_cli is running

1.3.4.2 enter `10`, to select option `10. Get test LPT`

- This can take up to 10 minutes to arrive, but often happens in seconds, maybe faster
- You can verify whether you have received the LPT using option 1 in livepeer_cli - `Get node status`, and look for `LPT Balance`
- Also, you can use https://rinkeby.etherscan.io to view the details of your ETH Account. There should now be 2 transactions

1.3.5 Validate that you have received the LPT

1.3.5.1 enter `1` into livepeer_cli

1.3.5.2 verify that the `LPT Balance` is positive

- If you do not have any LPT in your account, contact the Livepeer Team at http://gitter.im/livepeer and someone there will be happy to help you get some test LPT.

1.3.6 deposit ETH into your broadcaster account

- this deposit covers your broadcasting costs

1.3.6.1 enter `13` into livepeer_cli to select `13. Deposit (ETH)`

1.3.6.2 enter an amount you would like to deposit, and press return

- This can take _up to 10 minutes_ to arrive, but often happens `in seconds`, _maybe faster_
- You can use https://rinkeby.etherscan.io to view the details of your ETH Account. There should now be 3 transactions

You are now ready to broadcast on Livepeer.

2. Download and install OBS

- follow the instructions provided by OBS Project at http://obsproject.com.

3. Configure OBS to broadcast on Livepeer:

3.1 launch OBS software

- if you are opening for the first time, cancel the configuration wizard

3.2 Click "Settings" in the bottom right hand corner of the screen.

3.3 Select "Stream" from the menu on the left of the "Settings" window

3.4 Under "Stream Type" select "Custom Streaming Server"

v) for URL, put rtmp://localhost:1935

vi) Click "OK" to close the "Settings" window

4. Start broadcasting and monitoring

4.1 Ensure livepeer is running (see above)

4.1 Click "Start Streaming" in OBS.

4.2 Open https://media.livepeer.org/ in a web browser

4.3 Paste the Ethereum address into the Search field, and click "SEARCH"

You should be broadcasting a blank screen.

After this, you are free to stream whatever content you want to configure in OBS.

Personally, I like to add a simple "Hello World" text source to the default scene in OBS
