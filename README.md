# Multithreaded TCP Chat in C

A command-line client–server chat project using IPv4 TCP sockets and POSIX threads.

## Features

- Clients choose a name and send messages through the server.
- The server broadcasts incoming messages to other connected clients.
- The server starts one receiving thread per client.
- Each client receives messages in a separate thread while the main thread handles console input.
- Type `exit` to leave the chat.

## Project structure

- `SocketServer/main.c`: connection acceptance and message broadcasting.
- `SocketClient/main.c`: console input and message reception.
- `SocketUtil/`: shared socket and IPv4 address helpers.

## Environment

Written in C99 using POSIX sockets and pthreads. Intended for Linux or a compatible POSIX environment such as WSL. The server listens on port 2000; clients connect to `127.0.0.1:2000` by default.

The existing CMake files contain machine-specific library paths and need adjustment before building on another machine.

## Current limitations

This is a learning project. Thread entry-point signatures, synchronization of the shared client list, buffer bounds, disconnected-client cleanup, and TCP message framing need improvement. The server currently stores clients in a fixed array of 10 entries without enforcing its capacity.
