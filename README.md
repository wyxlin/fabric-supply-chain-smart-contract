# Hyperledger Fabric Supply Chain Smart Contract

A Go-based smart contract for supply chain asset management on Hyperledger Fabric.

---

## Overview

This project implements a supply chain management smart contract using Hyperledger Fabric and Go.  
It supports creating, updating, transferring, and querying product records stored on the blockchain ledger.

The smart contract models each product as an on-chain asset with metadata such as owner, status, category, description, and timestamps.

---

## Features

- Initialize the ledger with sample products  
- Create a new product on the ledger  
- Update product information with partial update logic  
- Transfer ownership of a product  
- Query a product by ID  
- Retrieve all products from the ledger  

---

## Tech Stack

- Go  
- Hyperledger Fabric  
- Docker / Docker Compose  
- Git  

---

## Data Model

Each product contains the following fields:

- `id`  
- `name`  
- `status`  
- `owner`  
- `created_at`  
- `updated_at`  
- `description`  
- `category`  

---

## Smart Contract Functions

### `InitLedger`
Seeds the ledger with two sample products:
- Laptop  
- Smartphone  

### `CreateProduct`
Creates a new product if the given ID does not already exist.

### `UpdateProduct`
Updates product fields such as status, owner, description, and category.  
This function supports partial updates by only modifying non-empty input fields.

### `TransferOwnership`
Changes the owner of an existing product.

### `QueryProduct`
Returns a single product by its ID.

### `GetAllProducts`
Returns all products currently stored in the ledger.

---

## Project Structure

    .
    ├── smartcontract.go
    └── README.md

---

## How It Works

This project uses Hyperledger Fabric chaincode to manage blockchain-backed product assets.

Typical flow:

1. A client invokes a smart contract function  
2. The chaincode executes the requested business logic  
3. Product data is written to or read from the ledger using Fabric APIs  
4. The ledger state is updated and shared across the network  

---

## Example Use Cases

- Track products through a supply chain workflow  
- Record ownership transfers between organizations  
- Maintain an immutable and traceable ledger of product states  

---

## Design Considerations

- Modeled products as on-chain assets with unique IDs to ensure traceability across the supply chain  
- Used transaction timestamps instead of local system time to maintain consistency across distributed peers  
- Implemented partial update logic to avoid overwriting existing fields when new values are not provided  
- Encapsulated ledger operations into helper functions (`putProduct`, `getProduct`) to improve code modularity and readability  

---

## Potential Enhancements

- Support querying products by owner or category  
- Implement product history tracking using Fabric APIs  
- Add validation rules for product state transitions (e.g., Manufactured → Shipped → Delivered)  
- Introduce access control for different participant roles  
- Integrate with a backend API layer or web-based frontend for end-to-end interaction  

---

## System Context

This smart contract represents the blockchain layer of a supply chain system.  

In a production environment, it would typically be integrated with:

- A backend service using the Fabric SDK to invoke contract functions  
- A frontend application for user interaction and visualization  
