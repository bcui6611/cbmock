Prerequisites
-------------

* Python 2.6
* pip

Installation
------------

    pip install cbmock

Source code dependencies
------------------------

    pip install twisted cbtestlib

Example
-------

First of all start mock server

    > cbmock

or

    > ./cbmock/cbmock.py

Train server to handle GET requests

    > curl 127.0.0.1:8091/test
    > Not found: '/test'

    > curl -d "path=/test&method=GET&response_code=200&response_body=2*2" 127.0.0.1:8080
    > Success

    > curl 127.0.0.1:8091/test
    > 4

Train server to handle parameterized POST requests

    > curl -d "path=/test&method=POST&response_code=200&response_body={param1}*{param2}" 127.0.0.1:8080
    > Success

    > curl -d "{param1}=2&{param2}=2" 127.0.0.1:8091/test
    > 4

You can start mock cluster as well:

    > cbmock --nodes=4

    > curl -d "path=/test&method=GET&response_code=200&response_body=2*2" 127.0.0.1:8080
    > Success

    > curl 127.0.0.1:9000/test
    > 4

    > curl 127.0.0.1:9003/test
    > 4

Testing
-------

    > pip install lettuce nose requests

    > lettuce
