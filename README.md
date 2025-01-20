# Unhandled 'error' event in Node.js HTTP server

This repository demonstrates a common but easily missed error in Node.js HTTP servers: the lack of proper error handling, leading to server crashes without informative logs.

## Bug

The `server.js` file contains a basic Node.js HTTP server.  However, it lacks a proper `'error'` event listener on the server object.  This means that if an error occurs during request handling (e.g., a database connection error), the server will crash without providing any details in the console.

## Solution

The `serverSolution.js` file demonstrates the correct way to handle errors.  An `'error'` event listener is added to the server to catch and log any errors, preventing unexpected crashes and providing valuable debugging information.

## How to reproduce

1. Clone the repository.
2. Run `node server.js`. 
3. The server will start successfully but if you cause an error (e.g. by having the server try to access a non-existent file), the server will abruptly terminate without useful error details.
4. Run `node serverSolution.js` to see a fixed version that handles the error gracefully.