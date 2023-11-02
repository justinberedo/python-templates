# Asynchronous I/O
- asyncio is a library to write concurrent code using the async/await syntax.
- asyncio is often a perfect fit for IO-bound and high-level structured network code.
- async IO is a style of concurrent programming, but it is not parallelism.
- Asynchronous routines are able to “pause” while waiting on their ultimate result and let other routines run in the meantime.
- Async IO takes long waiting periods in which functions would otherwise be blocking and allows other functions to run during that downtime.
- coroutine is a function that can suspend its execution before reaching return, and it can indirectly pass control to another coroutine for some time.

## Rules
```
async def f(x):
    y = await z(x)  # OK - `await` and `return` allowed in coroutines
    return y

async def g(x):
    yield x  # OK - this is an async generator

async def m(x):
    yield from gen(x)  # No - SyntaxError

def m(x):
    y = await z(x)  # Still no - SyntaxError (no `async def` here)
    return y
```