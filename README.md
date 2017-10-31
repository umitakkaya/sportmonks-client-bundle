SportMonks API Client Library
=============================

[![Build Status](https://travis-ci.org/hristonev/sportmonks-client-bundle.svg?branch=master)](https://travis-ci.org/hristonev/sportmonks-client-bundle)

## API Version support

This API Client supports SportMonks v2.0.

## Requirements

### Installation

`composer require hristonev/sportmonks-client-bundle`

## Configuration

``` php
// Bootstrap
require 'vendor/autoload.php';

use SportMonks\API\HttpClient as SportMonksAPI;

// Default values. Can be initialized without arguments.
$scheme = 'https';
$hostname = 'sportmonks.com';
$subDomain = 'soccer';
$port = 443;

// Auth.
$token = 'open sesame';

$client = new SportMonksAPI();

// Set auth.
$client->setAuth(Auth::BASIC, [
    'token' => $token
]);
```

## Usage example

### Paginated resource
``` php
$data = [];
do{
    $data = array_merge($data, $client->countries()->findAll());
}while($client->countries()->nextPage());
print_r($data);
```

## Reference

Basic methods find({id}), findAll(), nextPage(). nextPage() is used on paginated response.

- continents
- countries
- leagues
- seasons
    - find(id, true) `include results`