# BlockChainNetworkHomework

Setup Up instructions.


Initialize and create  accounts for the two nodes
Open a command promt terminal by typing 'cmd' in search window on a PC.
Assuming that you had installed the geth and puppeth tools and the executables are in your current folder.

To create accounts execute the following commands ( please dont setup a password for creating these accounts)
geth.exe account new --datadir nodel 
geth.exe account new --datadir node2

This will create 2 folders with the respective names of node1 and node2 in your current directory. 
Also from the prompt copy the public address of key and Path of secret file for both node1 and node2 in a notepad file for reference.

With the info above, now lets setup a genesis block using the instrucitons below:

Run `puppeth`, name your network as 'pupnetkbm' , , chainid value is 333 and select the option to configure a new genesis block.

* Choose the `Clique (Proof of Authority)` consensus algorithm.

* Paste both account addresses from the above( the ones we saved in a notepad file) one at a time into the list of accounts to seal.

* Paste them again in the list of accounts to pre-fund. There are no block rewards in PoA, so you'll need to pre-fund.

* Choose `no` for pre-funding the pre-compiled accounts (0x1 .. 0xff) with wei. This keeps the genesis cleaner.

* Complete the rest of the prompts, and when you are back at the main menu, choose the "Manage existing genesis" option.
pupnetkbm.json`.
* The screenshot of the pupnetkbm configuration is saved in the screenshots folder in the repo.

Initilaize the nodes to create the genesis state and some files for each node sing Geth tool.
 use the following commands
 geth.exe init pupnetkbm\pupnetkbm.json --datadir node1
 geth.exe init pupnetkbm\pupnetkbm.json --datadir node2 
 
 To start the first node for mining, execute the following command
 geth --datadir node1 --unlock "0x14E0a198B5DF4bbad89cbc94c1209248052c72db" --mine --rpc --allow-insecure-unlock
 geth --datadir node2 --unlock "0x0EF7D0324E34147ecBbFCDbbB65D5c08174ABaf4" --mine --port 30304 --bootnodes "enode://SEALER_ONE_ENODE_ADDRESS@127.0.0.1:30303" --ipcdisable --allow-insecure-unlock
 
 Note: the value of the bootnodes flag will be available once we start the node 1.
 
  With both nodes up and running, the blockchain can be added to MyCrypto for testing.

    * Open the MyCrypto app, then click `Change Network` at the bottom left:

    * Click "Add Custom Node", then add the custom network information that you set in the genesis.

    * Make sure that you scroll down to choose `Custom` in the "Network" column to reveal more options like `Chain ID`:

    * Type `ETH` in the Currency box.
    
    * In the Chain ID box, type the chain id you generated during genesis creation ( which was 333).

    * In the URL box type: `http://127.0.0.1:8545`.  This points to the default RPC port on your local machine.

    * Finally, click `Save & Use Custom Node`. 

7. After connecting to the custom network in MyCrypto, it can be tested by sending money between accounts.

    * Select the `View & Send` option from the left menu pane, then click `Keystore file`.
    
    * On the next screen, click `Select Wallet File`, then navigate to the keystore directory inside your Node1 directory, select the file located there, provide your password when prompted and then click `Unlock`.

    * This will open account wallet inside MyCrypto.    
   
    * In the `To Address` box, type the account address from Node2, then fill in an arbitrary amount of ETH:
  
    * Confirm the transaction by clicking "Send Transaction", and the "Send" button in the pop-up window.  

    * Click the `Check TX Status` when the green message pops up, confirm the logout:

    * The transaction will go from `Pending` to `Successful` in around the same blocktime.

    * You can click the `Check TX Status` button to update the status.

Check the screenshots folder for the successful transaction.

  
 

