# Celestial

This application requires familiarity with the fundamentals concepts of a Blockchain platform.
Concepts like:

    - Block
    - Blockchain
    - Wallet
    - Blockchain Identity
    - Proof of Existance

## About

@maqzi is trying to make a test of concept on how a Blockchain application can be implemented in his company.
He is an astronomy fan and spends most of his free time looking at stars in the sky, that's why he would like
to create a test application that allows him and some of his friends to register stars, making sure the application 
maintains the ownership records.

### Process

1. The application will create a Genesis Block when we start it.
2. The user will request the application to send a message to be signed using a Wallet and therefore verify the ownership over the wallet address. The message format will be: `<WALLET_ADRESS>:${new Date().getTime().toString().slice(0,-3)}:starRegistry`;
3. Once the user have the message the user can use a Wallet to sign the message.
4. The user will try to submit the Star object with the parameters: `wallet address`, `message`, `signature` and the `star` object with the star information.
    The Star data model is as follows:
    ```json
        "star": {
            "dec": "68° 52' 56.9",
            "ra": "16h 29m 1.0s",
            "story": "Testing the story 4"
		}
    ```
5. The application will verify if the time elapsed from the request ownership (the time is contained in the message) and the time when you submit the star is less than 5 minutes.
6. If everything is okay the star information will be stored in the block and added to the `chain`
7. The application will allow us to retrieve the Star objects belong to an owner (wallet address). 


### Requirements

- This application will be created using Node.js and Javascript programming language. The architecture will use ES6 classes
because it will help us to organize the code and facilitate the maintnance of the code.
- Some of the libraries or npm modules you will use are:
    - "bitcoinjs-lib": "^4.0.3",
    - "bitcoinjs-message": "^2.0.0",
    - "body-parser": "^1.18.3",
    - "crypto-js": "^3.1.9-1",
    - "express": "^4.16.4",
    - "hex2ascii": "0.0.3",
    - "morgan": "^1.9.1"
    Remember if you need install any other library you will use `npm install <npm_module_name>`

#### Libraries:

1. `bitcoinjs-lib` and `bitcoinjs-message`: will help us verify the wallet address ownership by verifying the signature.
2. `express`: The REST Api in this application is created using Express.js framework.
3. `body-parser`: this library will be used as middleware module for Express and will help us to read the json data submitted in a POST request.
4. `crypto-js`: This module contain some of the most important cryotographic methods and will help us to create the block hash.
5. `hex2ascii`: This library will help us to **decode** the data saved in the body of a Block.

## Steps
1. Clone this repo and navigate to the directory.
   
2. We shall install all dependencies next, to do that: open a terminal and run the command `npm install`.
**( Remember to be able to work on this project you will need to have installed in your computer Node.js and npm )**

3. At this point we are ready to run the application, use the command: `node app.js`. You can check in your terminal the the Express application is listening in the PORT 8000


## Testing

To test your application I recommend you to use POSTMAN, this tool will help you to make the requests to the API.
Always is useful to debug your code see what is happening in your algorithm, so I will let you this video for you to check on how to do it >https://www.youtube.com/watch?v=6cOsxaNC06c . Try always to debug your code to understand what you are doing.

1. Run your application using the command `node app.js`
You should see in your terminal a message indicating that the server is listening in port 8000:
> Server Listening for port: 8000

2. To make sure your application is working fine and it creates the Genesis Block you can use POSTMAN to request the Genesis block:
    ![Request: http://localhost:8000/block/0 ](https://s3.amazonaws.com/video.udacity-data.com/topher/2019/April/5ca360cc_request-genesis/request-genesis.png)
3. Make your first request of ownership sending your wallet address:
    ![Request: http://localhost:8000/requestValidation ](https://s3.amazonaws.com/video.udacity-data.com/topher/2019/April/5ca36182_request-ownership/request-ownership.png)
4. Sign the message with your Wallet:
    ![Use the Wallet to sign a message](https://s3.amazonaws.com/video.udacity-data.com/topher/2019/April/5ca36182_request-ownership/request-ownership.png)
5. Submit your Star
     ![Request: http://localhost:8000/submitstar](https://s3.amazonaws.com/video.udacity-data.com/topher/2019/April/5ca365d3_signing-message/signing-message.png)
6. Retrieve Stars owned by me
    ![Request: http://localhost:8000/blocks/<WALLET_ADDRESS>](https://s3.amazonaws.com/video.udacity-data.com/topher/2019/April/5ca362b9_retrieve-stars/retrieve-stars.png)
