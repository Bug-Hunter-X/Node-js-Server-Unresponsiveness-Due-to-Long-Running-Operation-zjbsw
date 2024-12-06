# Node.js Server Unresponsiveness

This repository demonstrates a common issue in Node.js servers: unresponsiveness caused by long-running operations that block the event loop.  The `server.js` file contains a simple HTTP server with a synchronous `while` loop that simulates a 5-second delay.  This blocks the event loop, preventing the server from responding to other requests during that time.  The solution, `serverSolution.js`, demonstrates how to fix the issue using asynchronous operations.

## Bug

The primary problem lies in the synchronous nature of the `while` loop within the request handler.  Node.js uses a single-threaded event loop to handle requests.  Blocking this loop with a synchronous operation prevents the server from responding to new requests until the operation completes.  This leads to unresponsiveness and potentially impacts the user experience negatively.

## Solution

The solution utilizes asynchronous operations to avoid blocking the event loop.  This allows the server to continue processing other requests while the long-running task is executed in the background.