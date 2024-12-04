# 🚗 Automobile Use Case Using Minifabric 🚗

Welcome to the **Automobile Lifecycle Management System**! This project demonstrates the tracking of **automobile manufacturing**, **ownership**, and **lifecycle status** using **Hyperledger Fabric** and **Minifabric**. With this system, you can ensure transparency and security in automobile tracking using blockchain technology.

---

## 📚 Table of Contents

1. [Overview](#overview)  
2. [Features](#features)  
3. [Prerequisites](#prerequisites)  
4. [Setup and Installation](#setup-and-installation)  
5. [Network Configuration](#network-configuration)  
6. [Smart Contract](#smart-contract)  
7. [Usage](#usage)  
8. [License](#license)  

---

## 🔍 Overview

This project leverages **Minifabric** to simplify the deployment and management of a **Hyperledger Fabric** network. It includes a **smart contract** that handles **CRUD operations** (Create, Read, Update, Delete) for managing car assets in the system.

The main objective of this system is to provide a decentralized, secure, and transparent platform for managing automobile lifecycle events.

---

## 🌟 Features

- **Asset Lifecycle Management**: Track the lifecycle of automobiles from manufacturing to ownership and status updates in real-time.
- **CRUD Operations**: Create, read, update, and delete car records with secure blockchain transactions.
- **Security & Privacy**: Strict access control using **MSP (Membership Service Providers)** to ensure only authorized users interact with the blockchain.
- **Channel-based Communication**: Enable secure communication among various participants (manufacturer, dealer, customer, etc.) via Hyperledger Fabric channels.

---

## 🛠️ Prerequisites

Ensure you have the following installed before setting up this project:

- [Minifabric](https://github.com/hyperledger/minifabric) – For quick deployment of Hyperledger Fabric networks
- [Docker](https://www.docker.com/get-started) and [Docker Compose](https://docs.docker.com/compose/) – For running the network containers
- [Go](https://golang.org/dl/) – For writing and running smart contracts
- [Node.js](https://nodejs.org/en/) – For any frontend or additional integration needs
- [Hyperledger Fabric CLI Tools](https://hyperledger-fabric.readthedocs.io/en/latest/) – For interacting with the Fabric network

---

## Setup and Installation

Follow these steps to set up the Minifabric network and deploy the automobile use case smart contract.

1. **Clone the Repository**:

    ```bash
    git clone https://github.com/your-repository/automobile-usecase.git
    cd automobile-usecase
    ```

2. **Install Minifabric**:

    Follow the [Minifabric installation guide](https://github.com/hyperledger/minifabric#installation) to install Minifabric on your machine.

3. **Start the Fabric Network**:

    Use Minifabric to deploy the Hyperledger Fabric network.

    ```bash
    minifab netup -s couchdb -e true -i 2.4.8 -o manufacturer.auto.com
    ```

    This command starts the network with CouchDB as the state database and Fabric version 2.4.8.

4. **Create the Channel**:

    After the network is up, create a channel for communication between network participants.

    ```bash
    minifab create -c autochannel
    ```

5. **Join Peers to the Channel**:

    Join all peers to the channel.

    ```bash
    minifab join -c autochannel
    ```

6. **Anchor Peer Update**:

    Update the anchor peer for the channel.

    ```bash
    minifab anchorupdate
    ```

7. **Profile Generation**:

    Generate the network profile for further interaction with the network.

    ```bash
    minifab profilegen -c autochannel
    ```

---

## Network Configuration

This setup utilizes **Minifabric** to create the following network components:

- **Peers**: 
  - `peer1.org0.example.com`
  - `peer2.org0.example.com`
  - `peer1.org1.example.com`
  - `peer2.org1.example.com`

- **Orderers**: 
  - `orderer1.example.com`
  - `orderer2.example.com`
  - `orderer3.example.com`

- **CA (Certificate Authorities)**: 
  - `ca1.org0.example.com`
  - `ca1.org1.example.com`

The **autochannel** is created for secure communication among participants in the network.

---
## 🚀 Usage

### 🛠️ Interacting with the Smart Contract:

Once the **Hyperledger Fabric network** is set up, you can invoke the **CarContract** functions using the Fabric CLI or through scripts. Below are some of the key operations you can perform with the contract:

#### 1. **Create a New Car Asset**  
Invoke the `CreateCar` function to add a new car asset to the blockchain. You will need to pass in the car's unique details such as carID, make, model, and year.

#### 2. **Read Car Asset Details**  
Use the `ReadCar` function to retrieve information about a specific car by providing its unique `carID`. This will return the car's make, model, year, and ownership details.

#### 3. **Delete a Car Asset**  
The `DeleteCar` function allows you to delete a car asset from the blockchain. You must provide the car’s unique `carID` to remove it from the system.

### 🔐 Access Control:

The contract ensures that only authorized users under the **`manufacturer-auto-com`** Membership Service Provider (MSP) can perform critical actions, such as creating or deleting car assets. This ensures that the lifecycle of car assets is secure and only approved participants can modify the records.

---

## 📜 License

This project is licensed under the **MIT License**. See the [LICENSE](LICENSE) file for details.

---
