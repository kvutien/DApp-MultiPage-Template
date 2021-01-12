### DApp-MultiPage-Template ###
>A template for Ethereum-based  DApp.

Forked from [https://github.com/pankeshpatel/DApp-MultiPage-Template](https://github.com/pankeshpatel/DApp-MultiPage-Template), January 12, 2021. It has the same folder structure as [kickstarter](https://github.com/far1s/ethereum-kickstarter), it is a coincidence? It is probably derived from the other and modified, because its last date is later. To be analysed to understand how to use `Factory` design pattern and ERC-721 Non Fungible Tokens. It uses React. It has not been touched since 2 years.

### A  directory layout

- `components`              --  common UI components of a web page such as header, footer  
- `ethereum`                --  ethereum files  
  - `build`                 --  compiled contracts
    - `<contract-name>.json`--  compiled contract of `<contract-name>.sol`
  - `contracts`             --  solidity contracts
    - `<contract-name>.sol` --  solidity file of smart contract
  - `<contract-name>.js`    --
  - `compile.js`            --  compiles `<contract-name>.sol` file and generates `<contract-name>.json` file
  - `deploy.js`             --   deploys the compiled contract onto Blockchain Network (e.g., Rinkeby)
  - `factory.js`            -- It tells web3 that a deployed copy of the contract exists.
  - `web3.js`               --  It configures web3 with a **Blockchain network provider** (in our case it is Rinkeby BC network) from metamask.
- `pages`                   --  this directory contains react components that get turned into visitable webpages
  - `index.js`              --  home page of application
- `test`                    --  test cases of smart contract
  - `<contract-name>.test.js`-- test case of the `<contract-name>`
- `package.json`          --  project information and list require dependencies for the project
- `routes.js`             --  list the routes of the project
- `server.js`             --  boot up `nextjs` server and tells to use `routes.js`
- `README.md`             --  readme file of the project
- `node_modules`          --  project dependencies

# Installation

- `npm init` to generate `package.json` file
- `npm install --save ganache-cli mocha solc@0.4.17 fs-extra web3@1.0.0-beta.35` to install dependencies
- `npm install --save truffle-hdwallet-provider@0.0.3` for deployment dependencies
- `npm install --save next@4.1.4 react react-dom` for `next.js` dependencies
- `npm install --save semantic-ui-react` for UI components
- `npm install --save semantic-ui-css` for semantic UI stylesheet
- `npm install --save next-routes` for routing

# User guide
- Step 1: write smart contract (`.sol` file) into Remix Editor
- Step 2: copy paste the smart contract (`.sol` file) into a file of `contracts` directory.
- Step 3: compile the contract using `compile.js`
- Step 4: test the contract using a file of a `test` directory. The contract is deployed on local network `ganache`
- Step 5: deploy the contract on a test network (e.g., Rinkeby).
- Step 6: extract the address of the deployed contract from console.
- Step 7: Copy the address into `contract-address.txt` file for future use.
- Step 8: Create React components into `pages` directory.
- Step 9 : configures web3 with a provider from metamask in `web3.js`
- Step 10: update `factory.js` file with a deployed contract address (specified in `contract-address.txt`)
- Step 11: Use factory instance in React components (in `pages` directory) to interact with a deployed contract

> Source of images: "Ethereum and Solidity: The Complete Developer's Guide" by Stephen Grider

### WebApp and Smart Contract Interaction ###

> This is an example of how factory pattern can be used to deploy different instances of a smart contract.

<p align="center">
<a href=""target="_blank">
<img src="https://github.com/pankeshpatel/DApp-MultiPage-Template/blob/master/resource/app-high-architecture.PNG" alt="Ethereum-based Web Application Architecture" width="550" height="280" border="10" />
</a>
</p>

### Smart contract compilation using solidity compiler

<p align="center">
<a href=""target="_blank">
<img src="https://github.com/pankeshpatel/DApp-MultiPage-Template/blob/master/resource/contract-compilation.PNG" alt="Ethereum-based Web Application Architecture" width="550" height="280" border="10" />
</a>
</p>

### ethereum/compile.js

<p align="center">
<a href=""target="_blank">
<img src="https://github.com/pankeshpatel/DApp-MultiPage-Template/blob/master/resource/compile-js-steps.PNG" alt="Ethereum-based Web Application Architecture" width="550" height="280" border="10" />
</a>
</p>

### Next.js

> `next.js` wraps `react.js` with some more functionalities such as routing, server-side rendering, hot module reload and so on.

<p align="center">
<a href=""target="_blank">
<img src="https://github.com/pankeshpatel/DApp-MultiPage-Template/blob/master/resource/nextjs.PNG"
alt="Ethereum-based Web Application Architecture" width="550" height="280" border="10" />
</a>
</p>

### pages
> this repository contains React components (as `.js` files) that get turned into visitable webpages.
When installed `.nextjs` (from `.next` folder) starts, it see the react components into `pages` directory
and turn each into routes (according to its directory path), as shown belowed.

<p align="center">
<a href=""target="_blank">
<img src="https://github.com/pankeshpatel/DApp-MultiPage-Template/blob/master/resource/pages.PNG"
alt="Ethereum-based Web Application Architecture" width="550" height="280" border="10" />
</a>
</p>

### web3 configuration (`/ethereum/web3.js`)
> Configure `web3` with a provider from a metamask.

<p align="center">
<a href=""target="_blank">
<img src="https://github.com/pankeshpatel/DApp-MultiPage-Template/blob/master/resource/web3-inject.PNG"
alt="Ethereum-based Web Application Architecture" width="550" height="280" border="10" />
</a>
</p>

> next.js rendering at the server. It renders the pages and sends the HTML code to the browser first,
then it sends javascript code to the browser.

<p align="center">
<a href=""target="_blank">
<img src="https://github.com/pankeshpatel/DApp-MultiPage-Template/blob/master/resource/nextjs-rendering.PNG"
alt="Ethereum-based Web Application Architecture" width="550" height="280" border="10" />
</a>
</p>

### web3 and contract (`/ethereum/factory.js`)
> It tells that a deployed copy of the contract on Rinkeby network exists

<p align="center">
<a href=""target="_blank">
<img src="https://github.com/pankeshpatel/DApp-MultiPage-Template/blob/master/resource/web3-contract.PNG"
alt="Ethereum-based Web Application Architecture" width="550" height="280" border="10" />
</a>
</p>

### nextjs page rendering at the server side

> The nextjs server renders the HTML page and sends the HTML pages to the browser.
`getInitialProps()` function is executed at nextjs server.

<p align="center">
<a href=""target="_blank">
<img src="https://github.com/pankeshpatel/DApp-MultiPage-Template/blob/master/resource/nextjs-page-rendering.PNG"
alt="Ethereum-based Web Application Architecture" width="550" height="280" border="10" />
</a>
</p>

### nextjs server (`server.js`) and `routes.js`

<p align="center">
<a href=""target="_blank">
<img src="https://github.com/pankeshpatel/DApp-MultiPage-Template/blob/master/resource/server.PNG"
alt="Ethereum-based Web Application Architecture" width="550" height="280" border="10" />
</a>
</p>
