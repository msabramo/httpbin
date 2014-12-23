httpbin(1): HTTP Request & Response Service
===========================================

Freely hosted in `HTTP <http://httpbin.org>`__,
`HTTPS <https://httpbin.org>`__ & `EU <http://eu.httpbin.org/>`__
flavors by `Runscope <https://www.runscope.com/>`__

|Build Status|

|Deploy to Heroku|

ENDPOINTS
---------

=======================================   =======
Endpoint                                  Description
---------------------------------------   -------
`/ <http://httpbin.org/>`_                This page.
`/response-headers <responseheaders>`_    Returns given response headers.
=======================================   =======

.. _responseheaders: http://httpbin.org/response-headers?Content-Type=text/plain;%20charset=UTF-8&Server=httpbin


-  ```/ip`` <http://httpbin.org/ip>`__ Returns Origin IP.
-  ```/user-agent`` <http://httpbin.org/user-agent>`__ Returns
   user-agent.
-  ```/headers`` <http://httpbin.org/headers>`__ Returns header dict.
-  ```/get`` <http://httpbin.org/get>`__ Returns GET data.
-  ``/post`` Returns POST data.
-  ``/patch`` Returns PATCH data.
-  ``/put`` Returns PUT data.
-  ``/delete`` Returns DELETE data
-  ```/gzip`` <http://httpbin.org/gzip>`__ Returns gzip-encoded data.
-  ```/deflate`` <http://httpbin.org/deflate>`__ Returns deflate-encoded
   data.
-  ```/status/:code`` <http://httpbin.org/status/418>`__ Returns given
   HTTP Status code.
-  ```/redirect/:n`` <http://httpbin.org/redirect/6>`__ 302 Redirects
   *n* times.
-  ```/redirect-to?url=foo`` <http://httpbin.org/redirect-to?url=http://example.com/>`__
   302 Redirects to the *foo* URL.
-  ```/relative-redirect/:n`` <http://httpbin.org/relative-redirect/6>`__
   302 Relative redirects *n* times.
-  ```/cookies`` <http://httpbin.org/cookies>`__ Returns cookie data.
-  ```/cookies/set?name=value`` <http://httpbin.org/cookies/set?k1=v1&k2=v2>`__
   Sets one or more simple cookies.
-  ```/cookies/delete?name`` <http://httpbin.org/cookies/delete?k1&k2>`__
   Deletes one or more simple cookies.
-  ```/basic-auth/:user/:passwd`` <http://httpbin.org/basic-auth/user/passwd>`__
   Challenges HTTPBasic Auth.
-  ```/hidden-basic-auth/:user/:passwd`` <http://httpbin.org/hidden-basic-auth/user/passwd>`__
   404'd BasicAuth.
-  ```/digest-auth/:qop/:user/:passwd`` <http://httpbin.org/digest-auth/auth/user/passwd>`__
   Challenges HTTP Digest Auth.
-  ```/stream/:n`` <http://httpbin.org/stream/20>`__ Streams *n*–100
   lines.
-  ```/delay/:n`` <http://httpbin.org/delay/3>`__ Delays responding for
   *n*–10 seconds.
-  ```/drip?numbytes=n&duration=s&delay=s&code=code`` <http://httpbin.org/drip?numbytes=5&duration=5&code=200>`__
   Drips data over a duration after an optional initial delay, then
   (optionally) returns with the given status code.
-  ```/html`` <http://httpbin.org/html>`__ Renders an HTML Page.
-  ```/robots.txt`` <http://httpbin.org/robots.txt>`__ Returns some
   robots.txt rules.
-  ```/deny`` <http://httpbin.org/deny>`__ Denied by robots.txt file.
-  ```/cache`` <http://httpbin.org/cache>`__ Returns 200 unless an
   If-Modified-Since or If-None-Match header is provided, when it
   returns a 304.
-  ```/cache/:n`` <http://httpbin.org/cache/60>`__ Sets a Cache-Control
   header for *n* seconds.
-  ```/bytes/:n`` <http://httpbin.org/bytes/1024>`__ Generates *n*
   random bytes of binary data, accepts optional *seed* integer
   parameter.
-  ```/stream-bytes/:n`` <http://httpbin.org/stream-bytes/1024>`__
   Streams *n* random bytes of binary data, accepts optional *seed* and
   *chunk\_size* integer parameters.
-  ```/links/:n`` <http://httpbin.org/links/10>`__ Returns page
   containing *n* HTML links.
-  ```/forms/post`` <http://httpbin.org/forms/post>`__ HTML form that
   submits to */post*
-  ```/xml`` <http://httpbin.org/xml>`__ Returns some XML

DESCRIPTION
-----------

Testing an HTTP Library can become difficult sometimes.
`RequestBin <http://requestb.in>`__ is fantastic for testing POST
requests, but doesn't let you control the response. This exists to cover
all kinds of HTTP scenarios. Additional endpoints are being considered.

All endpoint responses are JSON-encoded.

EXAMPLES
--------

$ curl http://httpbin.org/ip
~~~~~~~~~~~~~~~~~~~~~~~~~~~~

::

    {"origin": "24.127.96.129"}

$ curl http://httpbin.org/user-agent
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

::

    {"user-agent": "curl/7.19.7 (universal-apple-darwin10.0) libcurl/7.19.7 OpenSSL/0.9.8l zlib/1.2.3"}

$ curl http://httpbin.org/get
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

::

    {
       "args": {},
       "headers": {
          "Accept": "*/*",
          "Connection": "close",
          "Content-Length": "",
          "Content-Type": "",
          "Host": "httpbin.org",
          "User-Agent": "curl/7.19.7 (universal-apple-darwin10.0) libcurl/7.19.7 OpenSSL/0.9.8l zlib/1.2.3"
       },
       "origin": "24.127.96.129",
       "url": "http://httpbin.org/get"
    }

$ curl -I http://httpbin.org/status/418
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

::

    HTTP/1.1 418 I'M A TEAPOT
    Server: nginx/0.7.67
    Date: Mon, 13 Jun 2011 04:25:38 GMT
    Connection: close
    x-more-info: http://tools.ietf.org/html/rfc2324
    Content-Length: 135

$ curl https://httpbin.org/get?show\_env=1
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

::

    {
      "headers": {
        "Content-Length": "",
        "Accept-Language": "en-US,en;q=0.8",
        "Accept-Encoding": "gzip,deflate,sdch",
        "X-Forwarded-Port": "443",
        "X-Forwarded-For": "109.60.101.240",
        "X-Heroku-Dynos-In-Use": "1",
        "Host": "httpbin.org",
        "Accept": "text/html,application/xhtml+xml,application/xml;q=0.9,*/*;q=0.8",
        "User-Agent": "Mozilla/5.0 (X11; Linux i686) AppleWebKit/535.11 (KHTML, like Gecko) Chrome/17.0.963.83 Safari/535.11",
        "X-Request-Start": "1350053933441",
        "Accept-Charset": "ISO-8859-1,utf-8;q=0.7,*;q=0.3",
        "Connection": "keep-alive",
        "X-Forwarded-Proto": "https",
        "Cookie": "_gauges_unique_day=1; _gauges_unique_month=1; _gauges_unique_year=1; _gauges_unique=1; _gauges_unique_hour=1",
        "X-Heroku-Queue-Depth": "0",
        "X-Heroku-Queue-Wait-Time": "11",
        "Content-Type": ""
      },
      "args": {
        "show_env": "1"
      },
      "origin": "109.60.101.240",
      "url": "http://httpbin.org/get?show_env=1"
    }

Installing and running from PyPI
--------------------------------

You can install httpbin as a library from PyPI and run it as a WSGI app.
For example, using Gunicorn:

.. code:: bash

    $ pip install httpbin
    $ gunicorn httpbin:app

Or run it directly:

.. code:: bash

    $ python -m httpbin.core

Changelog
---------

-  0.2.0: Added an XML endpoint. Also fixes several bugs with unicode,
   CORS headers, digest auth, and more.
-  0.1.2: Fix a couple Python3 bugs with the random byte endpoints, fix
   a bug when uploading files without a Content-Type header set.
-  0.1.1: Added templates as data in setup.py
-  0.1.0: Added python3 support and (re)publish on PyPI

AUTHOR
------

A `Runscope Community Project <https://www.runscope.com/community>`__.
Originally created by `Kenneth Reitz <http://kennethreitz.com/>`__.

SEE ALSO
--------

https://hurl.it http://requestb.in http://python-requests.org

.. |Build Status| image:: https://travis-ci.org/Runscope/httpbin.svg
   :target: https://travis-ci.org/Runscope/httpbin
.. |Deploy to Heroku| image:: https://camo.githubusercontent.com/c0824806f5221ebb7d25e559568582dd39dd1170/68747470733a2f2f7777772e6865726f6b7563646e2e636f6d2f6465706c6f792f627574746f6e2e706e67
   :target: https://heroku.com/deploy?template=https://github.com/Runscope/httpbin
