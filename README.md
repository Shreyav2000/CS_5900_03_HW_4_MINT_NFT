# Link to public repository
[Link](https://github.com/Shreyav2000/CS_5900_03_HW_4_MINT_NFT)


# Instructions

1. Requires Python 3, which may be installed via a variety of internet sites depending on your platform if you don't already have it.
2. Set a virtual environment with `Python3 -m venv venv`
3. Initialize your virtual environment with `source venv/bin/activate` (For Mac and Linux).
4. Install the dependencies with `pip install -r requirements.txt`
5. Play with it

# NFT MINT

- What we have here is a `run.py` in a flask app that runs our app, and will trigger everything that we have under the app directory.
- The file `Index.html` contains all the elements that are needed for the App
- In this case, we have some interaction buttons to interact with metamask
- For nft minter, we need to have the name of the nft and the description and the file type which is the most important field .
- When we upload our file element, the nft minter will upload it and mint it
- And once our logic runs, we display the result of the transaction that triggers our nft minting when we trigger our result.

# Logic File

- When you mint an nft, the main thing that you deal with is linking the token with the metadata.
- The token has the owner information, and because it has that information in the blockchain, the metadata identifies the object there.
- In order to do that we need to have access to the ipfs which is the leading solution for having decentralized storage in the blockchain. We can do this using the Moralis.
- We have a function here called upload and it gets triggered when we click upload. It will then collect the element by id of our file component that we have in our html. That component will capture files in an array.
- For this reason we point to the element 0, because we only want the first file that is captured by that interaction.
- `.saveIPFS()` is a Moralis function that is saving the Moralis object that we created to ipfs
- We are deactivating few elements in the middle so that no one can click on those elements on the website.
- The process has already started when we save our image to ipfs .
- After doing that, we are going to get :

1.  The hash of the file in ipfs which is the method that ipfs uses in order to identify that no single file is duplicated in their network
2.  The url which is to be provided by someone that has an ipfs gateway.

- We are creating a metadata object that is going to store everything regarding our nft . We are getting our element by id here, which is the name for the name of our nft , description and the image which is going to be represented by the image jury that we are getting from the Moralis in the previous step.
- Once we have all the metadata that is required, we are going to store that in `ipfs` by storing the json object.
- Then we have the new Moralis file ready that we can save it to ipfs to get ipfs url or jury. Using that, we can call our `mintToken function`. That mint token is interacting with a smart contract.
- The contract that we use are using here is present in the base contract file.
- We are sending a transaction to our `mintToken function`, and that transaction has to contain the encoded function call, so we are getting the api only for the function that we are calling with the parameter, and that will be encoded by the `mintToken functionality`.
- Then that encoded function goes to the transaction as a `transactionParameter` and further, we just send it to the blockchain.
- In the end When we get the transaction hash back, we know that the transaction has been processed. Henceforth, We can print to the user their transaction id which means that the nft is minted.
  #Output

1. Run the command `-run flask` to get the url of your mint nft
2. Go to the url link. The following output should be displayed:
   ![image](https://github.com/Shreyav2000/CS_5900_03_HW_4_MINT_NFT/blob/1591bee0368ee70d290fc603f02bcfb62a908ad3/Downloads/19_MINTNFT-master/Output.png)
3. Enter the username and Email and click on connect to MetaMask
4. It will then direct you to the MetaMask page
