# Raspberry Pi cluster computing project

The idea of many rpi's working together on one big project really entertains me.

I want to create a scalable network of a **server** and several **clients** to work together to complete a task such as **finding prime numbers** or computing steps in the **collatz conjecture**.

## Basic Concept

I know that I want the **server** to talk to many **clients** and distribute instructions and then collate the data that is returned from each **client**.

## Prime Numbers

The **server** is going to have a set of **clients** that it is going to talk to and distrbute instructions to and recieve data from.

### Job creation

The **server** will take a command to find prime numbers from a starting integer to and ending integer. The jobs will be based on another input, chunk size.

The command will take these arguments:

- Starting point
- Ending point
- Chunk size

### Client instructions

The instructions are going to be in the order of:

- Job ID
- Starting point
- Ending point
- Chunk size

### Job ID

The **server** will mainly use this to keep track of the data being returned and organize it in order incase that the jobs are not completed in the order that they were distributed.

### Starting point

### Ending point

### Chunk size