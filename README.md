### TornRPC ###
A tornado RPC library.

This RPC framework uses tornado
so its very quick and asynchronous.

This framework supports regular and
asynchronous methods to be registered
with the TornRPCServer. The below example
shows both. The only difference in the
framework is how you register it.
Normal functions are registered using
```server.register()```. Async functions
are registered using ```server.register_async()```.

For more detailed info see the docstring
for TornRPCClient and TornRPCServer.

For a real example of a server using this see https://github.com/sk8erwitskil/KVServer/blob/master/server.py

### install ###
```
pip install TornRPC
```
See https://pypi.python.org/pypi/TornRPC

### example server code ###
```python
from tornado import gen
from tornrpc.server import TornRPCServer

def test(arg):
  return "You said %s" % arg

@gen.coroutine
def testasync(arg):
  raise gen.Return("You said async %s" % arg)

server = TornRPCServer()
server.register(test)
server.register_async(testasync)
server.start(8080)
```
### example client code ###
```python
from tornrpc.client import TornRPCClient

client = TornRPCClient('localhost:8080')
print client.test('hi')
print client.testasync('hi')
```
