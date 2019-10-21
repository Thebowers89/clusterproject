# Raspberry Pi cluster computing project

The idea of many rpi's working together on one big project really entertains me.

I want to create a scalable network of a **server** and several **clients** to work together to complete a task such as **finding prime numbers** or computing steps in the **collatz conjecture**.

## Basic Concept

I know that I want the **server** to talk to many **clients** and distribute instructions and then collate the data that is returned from each **client**.

## Prime Numbers

**Created using Python**

The **server** is going to have a set of **clients** that it is going to talk to and distrbute instructions to and recieve data from.

### Job creation

The **server** will take a command to find prime numbers from a starting integer to and ending integer. The jobs will be based on another input, chunk size.

The command will take these arguments:

- Starting point
- Ending point
- Chunk size

The start and endpoints in the context of the **server** are considered the global start and endpoints. When the **server** distributes instructions, local start and endpoints are given to the **clients** as to not have duplicate jobs and to not have long response times in calculating data.

### Client instructions

The instructions are going to be in the order of:

- Job ID
- Starting point
- Ending point

The starting points and ending points are going to be computed by the **server** as determined by **chunk size**.

### Job ID

The **server** will mainly use this to keep track of the data being returned and organize it in order incase that the jobs are not completed in the order that they were distributed.

### Starting point

The starting point is the integer from which calculations will start.

### Ending point

The ending point is the integer that will signify the end of the calculations.

## Communication

### Rant area
Python's socket library will be used to handle communication between nodes.

I know how I want the packets to look going back and forth. I just dont know how I am going to have the **server** constantly cycle through each **client** in the **client list** to listen for data. I have read and Select.select() seems to be a possible solution.

Python also throws an error when any of the connected clients disconnects. I am going to need to look into fixing that.

### Packet construction

The packets are just going to be strings passed between nodes in two forms:

Server to Client:

`JobID:StartingPoint:EndingPoint`

The **client** will take the string and break it down by the ':' character. The JobID is stored to be returned later. A prime number finding function will be called with StartingPoint and EndingPoint, the results of which are stored to be returned to the **server**.

Client to Server:

`JobID:3,5,7,11,13...`

The **server** will take the string and break it down by the ':' character. The JobID is used to sort the data in a table of returned results. All of the numbers returned are turned into a list by breaking the string by ','.