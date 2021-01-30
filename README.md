# Creating a Proof of Authority Blockchain

## Step 0: Foundational Understanding

Proof of Authority blockchains are typically used for private networks because addresses require pre-approval (voting) to interact on the network. These approved acocunts are called "validators" and are hopefully incentivized to uphold correct transaction processes in order to retain their validator status. 

## Step 1: The Tools of the Trade

Geth--> aka "Go Ethereum," is one of the three original implementations of the Ethereum Protocol. You can install it on pretty much any operating system (or you can embed through a library). Click this link for download instructions (https://geth.ethereum.org/docs/install-and-build/installing-geth)

MyCrypto Wallet--> a software wallet that securely manages all of your Ethereum based tokens. We will be using Mycrypto connect to our homemade network! Click this link for download instructions (https://download.mycrypto.com/). 

Before we begin, you need to download both of these tools and save them somewhere easily available on your computer.

## Step 2: Approving the Validators

Since we are working with a PoA blockchain we must first initialize and approve two addresses to be validators. 

FYI, you need to be working within your Geth directory in order for your code to work!

```
    ./geth --datadir node1 account new
    ./geth --datadir node2 account new
```
I would advise saving the password in a .txt file in their respective node1/node2 folder.

Save the public key somewhere you can easily find it. 

## Step 3: The Genisis Block

This is where we will create our blockchain! If you are a BTC fan, this is the step where Satoshi included the now legendary quote: "The Times 03/Jan/2009 Chancellor on brink of second bailout for banks."

```
    ./puppeth
```
* Name your blockchain network something witty and personal (ex: etheremark, mchain, marktoken)
* Choose the Clicque PoA consensus algorithim (2)
* Paste the public addresses of Node1 and Node2 from step 2 one at a time into the list of accounts to seal
* Do the same thing when it asks for accounts to pre-fund
* Type "No" when it asks to pre-fund with 1 wei. 
* Choose a 3-5 digit Network ID and save it somewhere you can easily find (I put it in the addresses.txt file). We will use this in a few minutes
* Type in 2, manage existing genesis.
* Export the genesis configuration... this will fail with 2 of the files, but as long as networkname.json is exported you are good to go (type in 2)

## Step 4: Mining

Now that you have created the genesis block , you must initialize the nodes and start validating the blockchain!

* initalize the nodes with the new network
    ~~~
        ./geth --datadir node1 init blockchain_name.json
        ./geth --datadir node2 init blockchain_name.json
    ~~~
* in separate terminals inside the Geth directory you need to begin mining
    ~~~ 
        ./geth --datadir node1 --mine --minerthreads 1 --unlock "insert_public_address"   --password node1/password.txt --rpc --allow-insecure-unlock

        ./geth --datadir node2 --unlock insert_public_address --mine --port 30305 --bootnodes insert_enode --password node2/password.txt  --allow-insecure-unlock
    ~~~

## Step 5: Celebrate

Congratulations you have created a blockchain!!

## Step 6: Test Transactions
