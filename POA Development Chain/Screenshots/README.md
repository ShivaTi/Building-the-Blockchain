# Running a Proof of Authority Blockchain

The Proof of Authority (PoA) algorithm is typically used for private blockchain networks as it requires pre-approval of, or voting in of, the account addresses that can approve transactions (seal blocks).


1. Because the accounts must be approved, we will generate two new nodes with new account addresses that will serve as our pre-approved sealer addresses.

    -  Create accounts for two nodes for the network with a separate datadir for each using geth.

    - ```./geth --datadir node1 account new ```
    - ```./geth --datadir node2 account new```
    - where, --datadir value   is Data directory for the databases and keystore (default: "~/.ethereum")


2. Next, generate our genesis block.


    - Run puppeth, name the network as ```shivaagain```, and select the option to configure a new genesis block.


    - Choose the Clique (Proof of Authority) consensus algorithm.


    - Paste both account addresses from the first step one at a time into the list of accounts to seal.

  - ![Screenshot (482)](https://user-images.githubusercontent.com/73386878/111897507-54e40080-8a74-11eb-936e-9a841cd2daad.png)

    - Paste them again in the list of accounts to pre-fund. There are no block rewards in PoA, so we'll need to pre-fund.


    - we have to choose no for pre-funding the pre-compiled accounts (0x1 .. 0xff) with wei. This keeps the genesis cleaner.


    - Complete the rest of the prompts, and when you are back at the main menu, choose the "Manage existing genesis" option.


    - Export genesis configurations. This will fail to create two of the files, but you only need networkname.json. here, ```shivaagain.json``` is the required file.




3. With the genesis block creation completed, we will now initialize the nodes with the genesis' json file.

    - Using geth, initialize each node with the new networkname.json.

    -   ``` ./geth --datadir node1 init shivaagain.json ```
    - ```./geth --datadir node2 init shivaagain.json ```

     - where , --datadir value  is Data directory for the databases and keystore (default: "~/.ethereum") and   init  is to                        Bootstrap and initialize a new genesis block.




4. Now the nodes can be used to begin mining blocks.

    - Run the nodes in separate terminal windows with the commands:

    - ```./geth --datadir node1 --unlock "0x660e672eb6940896e3a6b5B2172373826613fB55" --mine --rpc --allow-insecure-unlock ```

    - ```./geth --datadir node2 --unlock "0x951a14010Daaa7f9BC265fFf89512E0DFf57182A" --mine --port 30304 --bootnodes "enode://0bb604b2bdcc53d8975ab29182d631dfc4dd92d8d4b7bc7044854196d729a40c43091d757a99ab4a19d8e7f4aecb0e2792f0cb62b841011578e59f5de5c25179@127.0.0.1:30303" --ipcdisable --allow-insecure-unlock ```

   - where,  --allow-insecure-unlock allow insecure account unlocking when account-related RPCs are exposed and  --ipcdisable                    Disable the IPC-RPC server and -mine   enable mining , --bootnodes value is Comma separated enode URLs for P2P discovery bootstrap and --port value is Network listening port (default: 30303)

5. our private PoA blockchain should now be running!


6. With both nodes up and running, the blockchain can be added to MyCrypto for testing. 
    - Open the MyCrypto app, then click Change Network at the bottom left:
    - Click "Add Custom Node", then add the custom network information that you set in the genesis.
    -  -  - ![Screenshot (488)](https://user-images.githubusercontent.com/73386878/111897714-a0e37500-8a75-11eb-9cdf-6d511338be4a.png)



    - Make sure that you scroll down to choose Custom in the "Network" column to reveal more options like Chain ID:

       
        - ![Screenshot (491)](https://user-images.githubusercontent.com/73386878/111897846-5e6e6800-8a76-11eb-98fa-8d35a96735fe.png)

    - Type ETH in the Currency box.
    - In the Chain ID box, type the chain id we generated during genesis creation which is 395.
    - In the URL box type: http://127.0.0.1:8545.  This points to the default RPC port on your local machine.
    - Finally, click Save & Use Custom Node.


7. After connecting to the custom network in MyCrypto, it can be tested by sending money between accounts.
    - Select the View & Send option from the left menu pane, then click Keystore file.

    - ![Screenshot (489)](https://user-images.githubusercontent.com/73386878/111898098-0e90a080-8a78-11eb-810e-dad8180e376b.png)

   -  On the next screen, click Select Wallet File, then navigate to the keystore directory inside your Node1 directory, select the file located there, provide your password when prompted and then click Unlock.


    

    - we will see the balance that was pre-funded for this account in the genesis configuration.

    - In the To Address box, type the account address from Node2 which is "0x951a14010Daaa7f9BC265fFf89512E0DFf57182A", then fill in an arbitrary amount of ETH:
    - - This will open your account wallet inside MyCrypto.
        - ![Screenshot (495)](https://user-images.githubusercontent.com/73386878/111897758-d38d6d80-8a75-11eb-8cee-dd17e0a4a43e.png)
    - Confirm the transaction by clicking "Send Transaction", and the "Send" button in the pop-up window.

    - Click the Check TX Status when the green message pops up, confirm the logout:


    - we should see the transaction go from Pending to Successful in around the same blocktime you set in the genesis.


    - we can click the Check TX Status button to update the status.

    - ![Screenshot (487)](https://user-images.githubusercontent.com/73386878/111897680-83aea680-8a75-11eb-8ae0-d9a3e1e17455.png)


   

.
    -

