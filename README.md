# KSM Faucet

## Instructions

Anyone can get KSM at the public faucet after genesis. Unlike test network tokens, we expect KSM to be a scarce resource and the faucet is designed to limit the amount of tokens distributed to each individual.

In order to prevent Sybil attacks, the faucet will only drip to users that have a GitHub account that was created prior to June, 21, 2019. If you do not have a GitHub account that was created prior to this date, please use the [KSM Request Form](https://docs.google.com/forms/d/e/1FAIpQLSfGAqjXY3xLokwl7A-R4JZAnrBnSI3BVXKMKDLCKVtHaxgs-w/formResponse) to request tokens.
### Requirements:

- Github account with a creation date **before** 21 June 2019
- The address that the user requests a drip to must have never received a drip in the past
- The GitHub user requesting the drip must not have received a drip from the faucet during the past 24 hours
- The address must contain the string `ksma` (case-insensitive)

### Step 1: Generate an Address

The faucet will only drip to addresses that contain the string `ksma`(case-insensitive, that is, `KSMA` or `kSmA` would work). It will also never drip to the same address twice. Thus, a new address has to be created each time a user requests KSM tokens.

Obtaining a valid address will require generating numerous addresses until you find one which meets the requirements. You can think of this as a small proof-of-work. You can use the command-line tool [Subkey](#Using-Subkey), the web interface ([PolkadotJS Dashboard](#Using-PolkadotJS-Dashboard)), or any other program capable of generating arbitrary addresses.  You can even code up your own if you like.


#### Using PolkadotJS Dashboard

1. Go to [Settings](https://polkadot.js.org/apps/#/settings) and select `Kusama (canary)` on the address network prefix drop-down list, then click `Save & Reload`.
![](https://i.imgur.com/Ci1SJvL.png)

2. Under the [Accounts page](https://polkadot.js.org/apps/#/accounts), select `Vanity Address` tab.
![](https://i.imgur.com/EZw5iOx.png)

3. Input `ksma` in the "search for" textbox and leave the "keypair crypto type" by default unless you want to use another type.  After this, click `Start generation`. It will most likely take at least 10 mins to generate the address pattern you want.
![](https://i.imgur.com/ckbunwK.png)


#### Using Subkey

#### Installation

You can install `subkey` with this one-line command:

```
cargo install --force --git https://github.com/paritytech/substrate subkey
```

Alternatively, you can build `subkey` from the source code.

1. Follow the build instructions for [Substrate](https://github.com/paritytech/substrate#6-building).
2. When building, build `subkey` by typing `cargo build -p subkey`.
3. The executable is `./target/debug/subkey`.

#### Usage

The command `subkey --network kusama vanity "ksma" --number 1` will generate a new key-pair where the address contains the string  `ksma`.

Depending on the hardware configuration of your computer and on luck, this computation may take anywhere from a few seconds to approximately 10 minutes.

```
$ subkey --network kusama vanity "ksma" --number 1
  Generating key containing pattern 'ksma'
  100000 keys searched; best is 190/237 complete
  200000 keys searched; best is 201/237 complete
  300000 keys searched; best is 207/237 complete
  ...
  1000000 keys searched; best is 225/237 complete
  2000000 keys searched; best is 225/237 complete
  best: 237 == top: 237
  Secret Key URI `0x6262bcafcf6e6abbea102a2dbafecb81c28e9737e2cbce3d3ead7bde47806ac4` is account:
  Public key (hex): 0xe6a979d75da9241c491f12b7e7c2cf015ba9202a4be4649a15b72a3a60e0e730
  Address (SS58): Hnksmako1TfL4rsVMnT798syHFdF8rtFQT3tNF4jqLdswZD
```

The `Address (SS58)` field is the Kusama address that you will need to request KSM to. Notice that the string `ksma` starts at the third character. Never share your `Secret Key`, as this controls your funds.

See the [`subkey` documentation](https://substrate.dev/docs/en/ecosystem/subkey) or enter `subkey --help` for more usage examples.

### Step 2: Submit an Issue

Once you have generated your Kusama address containing the string `ksma`, you are ready to request KSM from the faucet.

1. Log in to Github. Go to the [faucet repo](https://github.com/kusamanetwork/faucet/issues) of the Kusama Network organization.
2. Click on the Issues tab, then click "New Issue".
3. Enter any text for the "Title" textbox - it will be ignored.
4. In the "Leave a comment" textbox, enter the address you generated in Step 1 (which must include the string "ksma"). Do not enter any text other than this address.
5. Wait while the faucet verifies the address. Depending on network conditions and server load, this may take a few minutes, but should generally be complete within 30 seconds.
6. You will see a comment posted to your issue indicating success or failure.  Success means that 0.1 KSM has been sent to the posted address; failure means that there was some problem and no KSM was sent to your address. In the event of failure, the message should indicate what the problem is (e.g., the faucet is dry, the address is invalid).
7.  The issue will close automatically after you receive a response, whether or not it was a success.

### Notes:

- A single GitHub account can get 0.1 KSM every 24 hours.
- Remember to post _only the address_ - no other text, and definitely not your seed or mnemonic phrase!
- The total number of KSM available to _all users_ of the faucet is 10 KSM per day.

### Donations:

If you want to support the faucet, please send KSM to its wallet address: **EaG2CRhJWPb7qmdcJvy3LiWdh26Jreu9Dx6R1rXxPmYXoDk**

### Support:

If you are having difficulties using the faucet, please join the [Kusama Watercooler chat](https://matrix.to/#/%23kusamawatercooler%3Apolkadot.builders) and somebody will try to help you.
