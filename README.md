<!--

@license Apache-2.0

Copyright (c) 2018 The Stdlib Authors.

Licensed under the Apache License, Version 2.0 (the "License");
you may not use this file except in compliance with the License.
You may obtain a copy of the License at

   http://www.apache.org/licenses/LICENSE-2.0

Unless required by applicable law or agreed to in writing, software
distributed under the License is distributed on an "AS IS" BASIS,
WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
See the License for the specific language governing permissions and
limitations under the License.

-->


<details>
  <summary>
    About stdlib...
  </summary>
  <p>We believe in a future in which the web is a preferred environment for numerical computation. To help realize this future, we've built stdlib. stdlib is a standard library, with an emphasis on numerical and scientific computation, written in JavaScript (and C) for execution in browsers and in Node.js.</p>
  <p>The library is fully decomposable, being architected in such a way that you can swap out and mix and match APIs and functionality to cater to your exact preferences and use cases.</p>
  <p>When you use stdlib, you can be absolutely certain that you are using the most thorough, rigorous, well-written, studied, documented, tested, measured, and high-quality code out there.</p>
  <p>To join us in bringing numerical computing to the web, get started by checking us out on <a href="https://github.com/stdlib-js/stdlib">GitHub</a>, and please consider <a href="https://opencollective.com/stdlib">financially supporting stdlib</a>. We greatly appreciate your continued support!</p>
</details>

# Simple HTTP Server

[![NPM version][npm-image]][npm-url] [![Build Status][test-image]][test-url] [![Coverage Status][coverage-image]][coverage-url] <!-- [![dependencies][dependencies-image]][dependencies-url] -->

> Create a simple HTTP server.

<section class="installation">

## Installation

```bash
npm install @stdlib/net-simple-http-server
```

</section>

<section class="usage">

## Usage

```javascript
var httpServer = require( '@stdlib/net-simple-http-server' );
```

#### httpServer( \[options,] \[clbk] )

Creates a simple HTTP server.

<!-- run-disable -->

```javascript
// Serve from the current working directory of the calling process:
httpServer();
```

The function accepts the following options:

-   **dir**: directory from which to serve files.
-   **port**: server port. Default: `0` (i.e., randomly assigned).
-   **maxport**: max server port (used when port hunting). Default: `=port`.
-   **hostname**: server hostname.
-   **address**: server address. Default: `"0.0.0.0"`.
-   **open**: `boolean` indicating whether to launch a web browser.

By default, the server serves content from the current working directory of the calling process. To serve from an alternative directory (resolved relative to the current working directory), set the `dir` option.

<!-- run-disable -->

```javascript
var opts = {
    'dir': './examples'
};
httpServer( opts );
```

To obtain the `server` handle, provide a callback.

```javascript
var nextTick = require( '@stdlib/utils-next-tick' );

function onReady( error, server ) {
    if ( error ) {
        throw error;
    }
    nextTick( close );
    function close() {
        server.close();
    }
}
httpServer( onReady );
```

</section>

<!-- /.usage -->

<section class="examples">

## Examples

<!-- eslint no-undef: "error" -->

```javascript
var httpServer = require( '@stdlib/net-simple-http-server' );

var opts = {
    'dir': './',
    'port': 7331,
    'hostname': 'localhost',
    'open': false
};

httpServer( opts, clbk );

function clbk( error, server ) {
    if ( error ) {
        throw error;
    }
    // Give the user a few seconds to open her web browser before closing the server...
    setTimeout( onTimeout, 5000 );

    function onTimeout() {
        server.close();
    }
}
```

</section>

<!-- /.examples -->

* * *

<section class="cli">

## CLI

<section class="installation">

## Installation

To use as a general utility, install the CLI package globally

```bash
npm install -g @stdlib/net-simple-http-server-cli
```

</section>

<!-- CLI usage documentation. -->

<section class="usage">

### Usage

```text
Usage: simple-http-server [options] [dirpath]

Options:

  -h,    --help                Print this message.
  -V,    --version             Print the package version.
  -p,    --port port           Server port. Default: 0.
         --maxport maxport     Max server port. Default: `port`.
         --hostname hostname   Server hostname.
         --address address     Server address. Default: 0.0.0.0.
         --open                Launch a browser once server is ready.
```

The application recognizes the following [environment variables][environment-variable]:

-   `DEBUG`: enable verbose logging.
-   `PORT`: server port.
-   `MAXPORT`: max server port.
-   `HOSTNAME`: server hostname.
-   `ADDRESS`: server address.

</section>

<!-- /.usage -->

<section class="notes">

### Notes

-   Command-line arguments **always** take precedence over [environment variables][environment-variable].

</section>

<!-- /.notes -->

<section class="examples">

### Examples

To serve content from the current directory,

```bash
$ DEBUG=* simple-http-server
...
```

To serve content from an alternative directory,

```bash
$ DEBUG=* simple-http-server ./examples
...
```

</section>

<!-- /.examples -->

</section>

<!-- /.cli -->

<!-- Section for related `stdlib` packages. Do not manually edit this section, as it is automatically populated. -->

<section class="related">

</section>

<!-- /.related -->

<!-- Section for all links. Make sure to keep an empty line after the `section` element and another before the `/section` close. -->


<section class="main-repo" >

* * *

## Notice

This package is part of [stdlib][stdlib], a standard library for JavaScript and Node.js, with an emphasis on numerical and scientific computing. The library provides a collection of robust, high performance libraries for mathematics, statistics, streams, utilities, and more.

For more information on the project, filing bug reports and feature requests, and guidance on how to develop [stdlib][stdlib], see the main project [repository][stdlib].

#### Community

[![Chat][chat-image]][chat-url]

---

## License

See [LICENSE][stdlib-license].


## Copyright

Copyright &copy; 2016-2025. The Stdlib [Authors][stdlib-authors].

</section>

<!-- /.stdlib -->

<!-- Section for all links. Make sure to keep an empty line after the `section` element and another before the `/section` close. -->

<section class="links">

[npm-image]: http://img.shields.io/npm/v/@stdlib/net-simple-http-server.svg
[npm-url]: https://npmjs.org/package/@stdlib/net-simple-http-server

[test-image]: https://github.com/stdlib-js/net-simple-http-server/actions/workflows/test.yml/badge.svg?branch=main
[test-url]: https://github.com/stdlib-js/net-simple-http-server/actions/workflows/test.yml?query=branch:main

[coverage-image]: https://img.shields.io/codecov/c/github/stdlib-js/net-simple-http-server/main.svg
[coverage-url]: https://codecov.io/github/stdlib-js/net-simple-http-server?branch=main

<!--

[dependencies-image]: https://img.shields.io/david/stdlib-js/net-simple-http-server.svg
[dependencies-url]: https://david-dm.org/stdlib-js/net-simple-http-server/main

-->

[chat-image]: https://img.shields.io/gitter/room/stdlib-js/stdlib.svg
[chat-url]: https://app.gitter.im/#/room/#stdlib-js_stdlib:gitter.im

[stdlib]: https://github.com/stdlib-js/stdlib

[stdlib-authors]: https://github.com/stdlib-js/stdlib/graphs/contributors

[cli-section]: https://github.com/stdlib-js/net-simple-http-server#cli
[cli-url]: https://github.com/stdlib-js/net-simple-http-server/tree/cli
[@stdlib/net-simple-http-server]: https://github.com/stdlib-js/net-simple-http-server/tree/main

[stdlib-license]: https://raw.githubusercontent.com/stdlib-js/net-simple-http-server/main/LICENSE

[environment-variable]: https://en.wikipedia.org/wiki/Environment_variable

</section>

<!-- /.links -->
