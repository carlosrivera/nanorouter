NanoRouter
====

Simple router made to do quick and dirty test over PHP (primary API's developed on other platforms), not intented to be a production or complex framework but as a way to test simple stuff in an scenario with zero configurations.

## How to use it

``` php
// Load and create the router
require 'src/Router.php';

use \Nano\Router\Router;

$router = new Router();

// Add some routers, it support static and dynamic ones
$router->any('/', function() {
    echo "from index";
});

// For dynamic routes you can use regex or wildcards enclosed by <>
$router->get('/dynamic/<slug>/<id>', function($slug, $id) {
    echo "from dynamic with args: { slug: " . $slug . ", id: ". $id . "}";
});

// finally, just process the current route
$router->dispatch();
```

## Pretty URL's 

The main purpose of this library was to be able to route to pretty url's, to achieve this you can redirect all your request to your main file, or write the path after you script name `localhost/index.php/myroute/path`:


``` apache
RewriteEngine On
RewriteCond %{REQUEST_FILENAME} !-f
RewriteCond %{REQUEST_FILENAME} !-d
RewriteCond %{REQUEST_FILENAME} !-l
RewriteRule .* index.php [L,QSA]
```


## MIT Licence

Copyright (c) 2015 

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in
all copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT.  IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN
THE SOFTWARE.


