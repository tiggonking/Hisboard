# Electronic Health Record System on Blockchain

---

This project is based on a hyperledger fabric network (v2.0) that is managed by hospitals to securely store a patient's medical record while keeping the patient at the center of the process. This means that a patient's medical record cannot be accessed without their consent. All network participants - doctors, hospitals, pharmacies, and private clinics will be given digital certificates by the official medical board of the country to join the network. Doctors will have the ability to perform all the CRUD operations on their patient records.

This project is also useful in crisis situations like the COVID-19 outbreak by providing correct and auditable certificates to people. It also keeps track of those infected during the crisis or pandemic.

## Table of Contents

- [Installation](#Installation)
- [Contributing](#Contributing)
- [Project Status](#Status)
- [Tools and Technology Used](#Stack)
- [Google Docs](https://drive.google.com/open?id=1lrcfMYx-DvzWgwxbWq62cdAP2u8Pg0VP)

## Installation

### Install Docker

    > chmod +x docker.sh
    > sudo ./docker.sh
    > usermod -a -G docker ${USER}

### Start Local Test Fabric Network

    > cd CI
    > docker-compose up -d
    > docker exec -it cli bash
    > cd channel-artifacts && ./joinchannel.sh
    > cd $GOPATH/src/chaincode && go mod vendor
    > cd .. && peer lifecycle chaincode package health.tar.gz --label health -p chaincode
    > peer lifecycle chaincode install health.tar.gz
    > export CC_PACKAGE=health:----------64hexdigit number----------
    > peer lifecycle chaincode approveformyorg -C test -n health --package-id $CC_PACKAGE -v 1.0 -o orderer:7050 --sequence 1
    > peer lifecycle chaincode commit -C test -n health -v 1.0 -o orderer:7050 --sequence 1

### Start Hyperledger Explorer to view blocks

    > cd explorer
    > docker-compose up -d

> How to send Peer request

1. Feel free to add new/change mini-targets of the project in [Project Status](#Status) Section
2. Ensure that documentation is updated according to your changes.

## Status

### Blockchain

- :heavy_check_mark: Chaincode
  - :heavy_check_mark: Medical Report
  - :heavy_check_mark: Drugs
  - :heavy_check_mark: Tests
  - :heavy_check_mark: Treatment
  - :heavy_check_mark: Consent
- :white_large_square: Fabric Network configuration
  - :heavy_check_mark: Local Fabric Network for Test
  - :heavy_check_mark: Explorer to view metrics and visualize blocks
- :white_large_square: Fabric SDK [![Run in Postman](https://run.pstmn.io/button.svg)](https://app.getpostman.com/run-collection/a76327a3785763703ffc)
  - :white_large_square: Doctor Side
  - :white_large_square: Hospital Side
  - :white_large_square: Medical Board side
  - :white_large_square: Patient Side
  - :white_large_square: Certs Management

### Front-End

- :white_large_square: Doctor Side
- :white_large_square: Hospital Side
- :white_large_square: Medical Board side
- :white_large_square: Patient Side

### Back-End

- :white_large_square: PostgreSQL (Auto-increment Column)
- :white_large_square: Nodejs server

### Deployment

- :white_large_square: Containerization
  - :white_large_square: Blockchain
  - :white_large_square: Front-end
  - :white_large_square: Back-end
- :white_large_square: Kubernetes Orchestration
- :white_large_square: AWS
  - :white_large_square: Tested
  - :white_large_square: Deployed

## Stack

- Hyperledger Fabric (v2.0)
- Hyperledger Explorer
- Frontend (HTML, CSS,,)
- Golang
- PostgreSQL
- Nodejs
- Docker
- Kubernetes
- AWS (VPCs and EC2s)
