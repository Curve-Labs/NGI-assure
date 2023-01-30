# NGI Search

## Description

The repository contains two packages that repesent a Proof of Concept for creating and governing ecological datastores on distributed computing and storage infrastructure.  The repo is structured as a mono repo, with a package containing the backend logic and another package containing the frontend.

### Backend

At the core of the backend logic is the ecological datastore. It represents a geo location and can contain arbitrary data. Within this PoC anyone can set up a new datastore to represent some sort of ecological data provisioning (e.g. IoT, human-based data collection) in a specific location. Datastores can be registered with the geospatial data registry. When a datastore has been registered it becomes exposed to data consumers. This means that when a data consumers queries the system for ecological data from a specific location, the datastore, if it lies within the location, will be displayed to the consumer. Within this PoC, the data stored within the datastore is open source, but different monetization mechanisms are conceivable to reward and incentivize the porivions of ecological data. Currently, only the administrator of the geospatial registry can register new datastores, but through the use of the governance modules, which are also contained in this PoC, granular controls flows are conceivable.

### Frontend

At the core of the frontend is an interactive map component that allows users to create, edit, display ecological datastores drawing a polygon on the map and submitting the underlying geodata together with configurable metadata describing the datastore.

## Structure

This mono repo contains a 2 packages to create and govern geographical datastores:

- hardhat-ts: a hardhat typescript project
    - contains the backend logic to create, edit and query geographical entities
    - contains the backend logic to set up granular permissioning, access control and governance systems
    - contains scripts to deploy the system
- dapp: a React, Redux web application
    - allows anyone to create a new geographical entity and attach to it data stored on IPFS & Ceramic Network

```
NGI assure
└── packages
    ├── hardhat-ts
    └── frontend
```

## Getting Started

Clone the repository

Using SSH

```
git clone git@github.com:Curve-Labs/ie-bacalhau.git
```

Using HTTPS

```
git clone https://github.com/Curve-Labs/ie-bacalhau.git
```

## Prerequisites

### Global

- NodeJS [(Install NodeJS)](https://nodejs.org/en/download/)
- Yarn [(Install Yarn)](https://classic.yarnpkg.com/en/docs/install)

### Package: dapp

Setup .env file for dapp

Create an Infura Account and an Infura project with IPFS Service, copy packages/dapp/.env.sample to packages/dapp/.env and fill in the following fields:

REACT_APP_PROJECT_ID=

REACT_APP_PROJECT_SECRET=

#### Setup Metamask

To run locally, create a new profile in Chrome and open the Metamask plugin.

Import the test seed phrase: test test test test test test test test test test test junk

Under Networks click Show/hide test networks

Open Metamask Settings, Networks, and select Localhost 8545. Set chainId to 31337

Select Localhost 8545 network.

Notice: when running a Localhost node, you may receive this error: Nonce too high. Expected nonce to be 1 but got N. Note that transactions can't be queued when automining. As a fix, go to Settings, Advanced, and click Reset Account.

## Installation

To install the dependencies for this project, please run the command yarn install in your terminal. This command will install all the necessary packages required to run the application.

```
yarn install
```

## Run locally

### Hardhat Local Node

Open a terminal and run yarn hardhat:localnode

### Run dapp

Open packages/dapp/webpack.config.js and update devServer...host with your local IP Address.

Open a second terminal and run yarn dapp:start

Open your Chrome profile with test Metamask instance and go to https://YOURIPADDRESS:8080/

### Account

    Select Metamask and connect with the localhost node.

## Available Scripts

In the project directory, you can run:

### dapp

#### `yarn dapp:start`

Runs the app in development mode on <https://YOURIPADDRESS:8080/>

#### `yarn dapp:test`

Runs the React test watcher in an interactive mode.
By default, runs tests related to files changed since the last commit.

[Read more about testing React.](https://facebook.github.io/create-react-app/docs/running-tests)

#### `yarn dapp:webpack`

Builds the dapp for production to the `build` folder.
It correctly bundles React in production mode and optimizes the build for the best performance.

### hardhat-ts

#### `yarn hardhat:test`

Run the tests in the test directory

#### `yarn hardhat:watch`

Starts a local node, deploys system, updates the deployments/localhost folder with contract address and abi.

On contract update, will redeploy and update deployments folder.


