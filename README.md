# net

TCP networking module for Quadrate.

## Installation

```bash
quadpm install https://github.com/quadrate-lanuage/net
```

## Usage

```quadrate
use net

fn main() {
    // Server example
    8080 net::listen! -> server
    server net::accept! -> client
    client 1024 net::receive! -> data -> n
    client "Hello!" net::send! -> sent
    client net::close
    server net::close

    // Client example
    "localhost" 8080 net::connect! -> sock
    sock "Hello server!" net::send! -> sent
    sock 1024 net::receive! -> response -> n
    sock net::close
}
```

## Functions

### Server Operations

- `listen(port:i64 -- socket:i64)!` - Create server socket on port
- `accept(server:i64 -- client:i64)!` - Accept incoming connection

### Client Operations

- `connect(host:str port:i64 -- socket:i64)!` - Connect to remote host

### Data Transfer

- `send(socket:i64 data:str -- bytes:i64)!` - Send data
- `receive(socket:i64 max:i64 -- data:str bytes:i64)!` - Receive data

### Connection Management

- `shutdown(socket:i64 --)` - Shutdown socket for writing
- `close(socket:i64 --)` - Close socket

## Error Constants

- `ErrListen` (2) - Listen/bind failed
- `ErrAccept` (3) - Accept failed
- `ErrConnect` (4) - Connection failed
- `ErrSend` (5) - Send failed
- `ErrReceive` (6) - Receive failed
- `ErrInvalidArg` (7) - Invalid argument

## License

Apache-2.0
