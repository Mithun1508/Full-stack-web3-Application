# Build an Application with Solidity, thirdweb & React
This template extends from the Greeter contract template by building an application on top of the smart contract.


# Tools used in this template:

1)thirdweb Typescript and React SDKs to interact with our smart contract

2)Solidity, Hardhat, and thirdweb deploy to develop, test, and deploy our smart contract.



# Run the Application:

To run the web application, change directories into application:

cd application
Then, run the development server:

npm install # Install dependencies first

npm run dev
Visit the application at http://localhost:3000/.


How to use this template
This template has two components:

1) The smart contract development in the contract folder.
  
2)The web application in the application folder.


# Deploying the contract
To deploy the Greeter contract, change directories into the contract folder:

cd contract
Use thirdweb deploy to deploy the contract:

npm install # Install dependencies first

npx thirdweb deploy

Complete the deployment flow by clicking the generated link and using the thirdweb dashboard to choose your network and configuration.

# Using Your Contract
Inside the home page of the web application, connect to your smart contract inside the useContract hook:

// Get the smart contract by it's address
const { contract } = useContract("0x..."); // Your contract address here (from the thirdweb dashboard)



We configure the desired blockchain/network in the _app.js file; be sure to change this to the network you deployed your contract to.

// This is the chainId your dApp will work on.
const activeChainId = ChainId.Goerli;
Now we can easily call the functions of our Greeter contract, such as the greet and setGreeting contract by using the useContractData hook to read, and the useContractCall hook to write data.

// Read the current greeting
const { data: currentGreeting, isLoading } = useContractData(contract, "greet");

// Write a new greeting
const { mutate: writeGreeting, isLoading: isWriting } = useContractCall(
  
  contract,
  
  "setGreeting"
);
# Connecting to user wallets
To perform a "write" operation (a transaction on the blockchain), we need to have a connected wallet, so we can use their signer to sign the transaction.

To connect a user's wallet, we use one of thirdweb's wallet connection hooks. The SDK automatically detects the connected wallet and uses it to sign transactions. This works because our application is wrapped in the ThirdwebProvider, as seen in the _app.js file.

