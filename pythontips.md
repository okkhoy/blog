# Python tips and tricks

## How to handle exceptions?

We know that one of ways to get python to be fast is to use `try ... except`, following the idea, better to ask for forgiveness than permission. The question remains, how to handle *any* exception the right way? How to log the exception for later use?

One of the usual suggestions is not to catch a generic exception, since it is too broad, but to catch only what can go wrong and handle it. In many situations that I have encountered, this may not be the ideal case. For instance, while writing to a file you handle `IOError`, but unknown to you there is a `TypeError` as well that can halt your program. Now how to handle `TypeError` that is not caught by the `except statement?`

In this snippet, we will address the same!

```python
try:
    some_function()
except Exception as ex:
    template = "An exception of type {0} occured. Arguments:\n{1!r}"
    message = template.format(type(ex).__name__, ex.args)
    print message
```

First thing to do is never have an empty `except` statement, but catch an exception. The exception object gives us a lot of information. `type` information is available via Python's `type()` call (`type(ex).__name__` gives the name of the exception that occured in the above snippet), the arguments (`ex.args` in the above snippet) contain details of the exception that occurred. This works for any custom exceptions that you implement.