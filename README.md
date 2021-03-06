liblifthttp - The fast asynchronous C++17 HTTP client library
=============================================================

You're using curl? Do you even lift?

Copyright (c) 2017, Josh Baldwin

https://github.com/jbaldwin/liblifthttp

**liblifthttp** is a C++17 client library that provides an easy to use high throughput asynchronous HTTP request client library.  This library was designed with an easy to use client API and maximum performance for thousands of asynchronous HTTP requests on a single (or multiple) worker threads.  Additional HTTP requests can be injected into one of the worker threads with different timeouts at any point in time safely.  The asynchronuos API can perform upwards of 30,000 HTTP requests / second on a single 2.8GHZ core.

**liblifthttp** is licensed under the Apache 2.0 license.

# Overview #
* Synchronous and Asynchronous HTTP Request support.
* Easy and safe to use C++17 Client library API.
* Background IO thread for sending and receiving HTTP requests.
* Request pooling for re-using HTTP requests.

# Usage #

## Requirements
    C++17 compiler (g++/clang++)
    CMake
    pthreads/std::thread
    libcurl
    libuv

## Instructions

### Building
    # This will produce lib/liblifthttp.a and bin/liblifthttp_test + all the examples
    mkdir Release && cd Release
    cmake -DCMAKE_BUILD_TYPE=Release ..
    cmake --build . -- -j4 # change 4 to number of cores available

## Examples

See all of the examples under the examples/ directory.

### Simple Synchronous

    lift::initialize();

    lift::RequestPool request_pool;
    auto request = request_pool.Produce("http://www.example.com");
    std::cout << "Requesting http://www.example.com" << std::endl;
    request->Perform();
    std::cout << request->GetResponseData() << std::endl;

    lift::cleanup();

### Simple Asynchronous

See [Async Simple](https://github.com/jbaldwin/liblifthttp/blob/master/examples/async_simple.cpp)

## Support

File bug reports, feature requests and questions using [GitHub Issues](https://github.com/jbaldwin/liblifthttp/issues)
