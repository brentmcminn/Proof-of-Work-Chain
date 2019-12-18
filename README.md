# Proof-of-Work-Chain
Testnet Blockchain with Instructions for use 

## We were successful in building a Proof of Authority testnet blockchain. This project involved running Geth commands, sending transactions from MyCrypto and lots of Geth CLI operations. 

## Instructions 

The POA blockchain testnet involved different steps than the POW setup. The difference was obvious from the beginning when we first created the two nodes using geth. After both nodes were set up, we created a genesis block using puppeth. This was a simple process where we put in both node addresses for the list of accounts to seal and for ths list of accounts to pre-fund. Following that, we set the chain id to 1234, we named our genesis block dualpoa. After the setup process was complete we exported the Genesis block configurations into a dualpoa.json file. 

Next we initialized each node using geth on both json files ./geth init dualpoa.json --datadir node1/ AND ./geth init dualpoa.json --datadir node2/   

Next we started mining with the first node using this CLI operation ./geth --datadir node1 --mine --rpc -unlock '0x65598Db05930F4A32800A05eef186D7264AB85c4' --minerthreads 1 --allow-insecure-unlock --password node1/password.txt --syncmode 'full' 

Since the first node was running, we opened another gitbash terminal and used this CLI operation using the 1st node's enode as the bootnode flag. 
./geth --datadir node2 --port 30304 --bootnodes 'enode://4e3893f216f574079487084841c4165f9d8812c81e39ea7c3ee53264df84c0afdb099d4b713855d2b54d28ec310da616c21ff8f5fd4894003d6469bd76f2328d@127.0.0.1:30303' --mine -unlock '0xd7048C09fDed6993A9d795C756b33272Cf4695D0' --minerthreads 1 --allow-insecure-unlock --password node2/password.txt --ipcdisable --syncmode 'full'

Then we opened MyCrypto and started a Custom Network whereI used my chain id and used ETH as currency. 
I imported my keystore file for node1 which was inside node1/keystore/

Lastly to send a transaction we add node2 address into the wallet address and show confirmation. 


