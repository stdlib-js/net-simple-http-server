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

# Simple HTTP Server

[![NPM version][npm-image]][npm-url] [![Build Status][test-image]][test-url] [![Coverage Status][coverage-image]][coverage-url] <!-- [![dependencies][dependencies-image]][dependencies-url] -->

> Create a simple HTTP server.



<section class="usage">

## Usage

```javascript
import httpServer from 'https://cdn.jsdelivr.net/gh/stdlib-js/net-simple-http-server@deno/mod.js';
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
import nextTick from 'https://cdn.jsdelivr.net/gh/stdlib-js/utils-next-tick@deno/mod.js';

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
import httpServer from 'https://cdn.jsdelivr.net/gh/stdlib-js/net-simple-http-server@deno/mod.js';

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



<!-- Section for related `stdlib` packages. Do not manually edit this section, as it is automatically populated. -->

<section class="related">

</section>

<!-- /.related -->

<!-- Section for all links. Make sure to keep an empty line after the `section` element and another before the `/section` close. -->


<section class="main-repo" >

* * *

## Notice

This package is part of [stdlib][stdlib], a standard library with an emphasis on numerical and scientific computing. The library provides a collection of robust, high performance libraries for mathematics, statistics, streams, utilities, and more.

For more information on the project, filing bug reports and feature requests, and guidance on how to develop [stdlib][stdlib], see the main project [repository][stdlib].

#### Community

[![Chat][chat-image]][chat-url]

---

## License

See [LICENSE][stdlib-license].


## Copyright

Copyright &copy; 2016-2022. The Stdlib [Authors][stdlib-authors].

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

[umd]: https://github.com/umdjs/umd
[es-module]: https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Modules

[deno-url]: https://github.com/stdlib-js/net-simple-http-server/tree/deno
[umd-url]: https://github.com/stdlib-js/net-simple-http-server/tree/umd
[esm-url]: https://github.com/stdlib-js/net-simple-http-server/tree/esm

[chat-image]: https://img.shields.io/gitter/room/stdlib-js/stdlib.svg
[chat-url]: https://gitter.im/stdlib-js/stdlib/

[stdlib]: https://github.com/stdlib-js/stdlib

[stdlib-authors]: https://github.com/stdlib-js/stdlib/graphs/contributors

[stdlib-license]: https://raw.githubusercontent.com/stdlib-js/net-simple-http-server/main/LICENSE

[environment-variable]: https://en.wikipedia.org/wiki/Environment_variable

</section>

<!-- /.links -->
