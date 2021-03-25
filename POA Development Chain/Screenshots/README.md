# How to start the Network

Start node1 in a terminal windows


-./geth --datadir node1 --unlock "0x660e672eb6940896e3a6b5B2172373826613fB55" --mine --rpc --allow-insecure-unlock 

Enter password = anuska-1

Start node2 in a separate terminal windows
    -./geth --datadir node2 --unlock "0x951a14010Daaa7f9BC265fFf89512E0DFf57182A" --mine --port 30304 --bootnodes "enode://0bb604b2bdcc53d8975ab29182d631dfc4dd92d8d4b7bc7044854196d729a40c43091d757a99ab4a19d8e7f4aecb0e2792f0cb62b841011578e59f5de5c25179@127.0.0.1:30303" --ipcdisable --allow-insecure-unlock 

 again enter password = anuska-1

 ![Screenshot (482)](https://user-images.githubusercontent.com/73386878/112415905-c96eb600-8d78-11eb-94cd-2cbbfb054cb5.png)

## Explanation of the flags

--datadir value: Data directory for the databases and keystore (default: "~/.ethereum")

--unlock value: Comma separated list of accounts to unlock

The --mine flag tells the node to mine new blocks.

--rpc flag enables us to talk to the first node, which will allow us to use MyCrypto to transact on our chain.

--allow-insecure-unlock flag allows insecure account unlocking when account-related RPCs are exposed by http

Since the first node's sync port already took up 30303, we need to change this one to 30304 using --port

The --bootnodes flag allows you to pass the network info needed to find other nodes in the blockchain. This will allow us to connect both of our nodes.

In Microsoft Windows, we need to add the flag --ipcdisable. Due to the way Windows spawns new IPC/Unix sockets, it doesn't allow for having multiple sockets running from geth at once. Since we are only using RCP we can safely disable the IPC sockets.

## Configuration of the network

Chain ID = 395
Account password = anuska-1
blocktime = 10 s

ports:
node1 = 30303
node2 = 30304


## How to send a transaction 

Open MyCrypto wallet
Set up a custom network
Node Name: shivaagain
Network: Custom
Network Name: shivaagain
Currency: ETH
Chain ID: 395
URL: http://127.0.0.1:8545
Import the keystore file from the node1/keystore directory into MyCrypto (Password: anuska-1). This will import the private key.
Send a transaction from the node1 account (Address:0x660e672eb6940896e3a6b5B2172373826613fB55 ) to the node2 account (Address:0x951a14010Daaa7f9BC265fFf89512E0DFf57182A ).


 -  -  - ![Screenshot (488)](https://user-images.githubusercontent.com/73386878/111897714-a0e37500-8a75-11eb-9cdf-6d511338be4a.png)

       
 After connecting to the custom network in MyCrypto, it can be tested by sending money between accounts.
- Select the View & Send option from the left menu pane, then click Keystore file.

- ![Screenshot (489)](https://user-images.githubusercontent.com/73386878/111898098-0e90a080-8a78-11eb-810e-dad8180e376b.png)
.
    
- we will see the balance that was pre-funded for this account in the genesis configuration.

- In the To Address box, type the account address from Node2 which is "0x951a14010Daaa7f9BC265fFf89512E0DFf57182A", then fill in an arbitrary amount of ETH:
 - - This will open your account wallet inside MyCrypto.
        - ![Screenshot (495)](https://user-images.githubusercontent.com/73386878/111897758-d38d6d80-8a75-11eb-8cee-dd17e0a4a43e.png)
- Confirm the transaction by clicking "Send Transaction", and the "Send" button in the pop-up window.

- Click the Check TX Status when the green message pops up, confirm the logout:


- we should see the transaction go from Pending to Successful in around the same blocktime you set in the genesis.


- we can click the Check TX Status button to update the status.

- ![Screenshot (487)](https://user-images.githubusercontent.com/73386878/111897680-83aea680-8a75-11eb-8ae0-d9a3e1e17455.png)


   


    -

