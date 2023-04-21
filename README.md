# Gift List

## Description

This project is aimed at practical blockchain development. We use Merkle Trees and cryptography to authenticate a user using proof verification on the server. If the user is on the list, a gift is given. Otherwise not.
It consists of a client and server architecture where the server is instantiated by typing: node server/index.js from the command line. Similarly, the client can be started by typing: node client/index.js (also from the command line in another terminal tab).

This starts a process, first in the client generating names and proofs that will be sent for verification... 
The following attempts were made:

- A name which is not in the list.
- A name which is on the list, with a proof that does not verify.
- A name which is on the list with a valid proof.

The list of names is in utils/niceList.json and utils/MerkleTree.js contains the implementation of the Merkle Tree. Instead of storing the whole list, we only store this Merkle tree's root (which is a hash), thus saving valuable space on the blockchain!


To get started with the repository, clone it and then run `npm install` in the top-level directory to install the depedencies.

There are three folders in this repository:

## Client

You can run the client from the top-level directory with `node client/index`. This file is a script which will send an HTTP request to the server.

Think of the client as the _prover_ here. It needs to prove to the server that some `name` is in the `MERKLE_ROOT` on the server. 

## Server

You can run the server from the top-level directory with `node server/index`. This file is an express server which will be hosted on port 1225 and respond to the client's request.

Think of the server as the _verifier_ here. It needs to verify that the `name` passed by the client is in the `MERKLE_ROOT`. If it is, then we can send the gift! 

## Utils

There are a few files in utils:

- The `niceList.json` which contains all the names of the people who deserve a gift this year (this is randomly generated, feel free to add yourself and others to this list!)
- The `example.js` script shows how we can generate a root, generate a proof and verify that some value is in the root using the proof. Try it out from the top-level folder with `node/example.js`
- The `MerkleTree.js` should look familiar from the Merkle Tree module! This one has been modified so you should not have to deal with any crypto type conversion. You can import this in your client/server
- The `verifyProof.js` should also look familiar. This was the last stage in the module. You can use this function to prove a name is in the merkle root, as show in the example.
