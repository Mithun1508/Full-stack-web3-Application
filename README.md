# Build an Application with Solidity, thirdweb & React
This template extends from the Greeter contract template by building an application on top of the smart contract.


# Tools used in this template:

1)thirdweb Typescript and React SDKs to interact with our smart contract

2)Solidity, Hardhat, and thirdweb deploy to develop, test, and deploy our smart contract.

# Getting Started

Create a project using this example:

```bash
npx create-tw-app --example next-javascript-starter
```

You can start editing the page by modifying `pages/index.js`. The page auto-updates as you edit the file.

On `pages/_app.js`, you'll find our `ThirdwebProvider` wrapping your app, this is necessary for our hooks to work.

on `pages/index.js`, you'll find the `useMetamask` hook that we use to connect the user's wallet to MetaMask, `useDisconnect` that we use to disconnect it, and `useAddress` to check the user's wallet address once connected. 



# Run the Application:

To run the web application, change directories into application:

cd application
Then, run the development server:

npm install # Install dependencies first

npm run dev
Visit the application at http://localhost:3000/.


# How to use this template
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

#References
- [thirdweb React Documentation](https://docs.thirdweb.com/react) - learn about our React SDK.

- [thirdweb JavaScript Documentation](https://docs.thirdweb.com/react) - learn about our JavaScript/TypeScript SDK.

- [thirdweb Portal](https://docs.thirdweb.com/react) - check our guides and development resources.

- [Next.js Documentation](https://nextjs.org/docs) - learn about Next.js features and API.
 
-You can check out [the thirdweb GitHub organization](https://github.com/thirdweb-dev)
