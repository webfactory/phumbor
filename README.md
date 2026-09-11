# Phumbor

A minimal PHP client for generating [Thumbor](https://github.com/globocom/thumbor) URLs.

This repo was forked out of the [original 99designs/phumbor](https://github.com/99designs/phumbor) library after the 1.2.2 release.

[![Build Status](https://travis-ci.org/webfactory/phumbor.svg?branch=main)](https://travis-ci.org/webfactory/phumbor)

## Usage

You construct a `Thumbor\Url` using a `Thumbor\Url\Builder`:

```php
$server = 'http://thumbor.example.com:1234';
$secret = 'my-secret-key';

echo Thumbor\Url\Builder::construct($server, $secret, 'http://images.example.com/llamas.jpg')
    ->fitIn(640, 480)
    ->addFilter('fill', 'green');

// => http://thumbor.example.com:1234/OFDRoURwi9WVbZNfeOJVfIKr1Js=/fit-in/640x480/filters:fill(green)/http://images/example.com/llamas.jpg
```

To reuse your server/secret combination, create a `Thumbor\Url\BuilderFactory`:

```php
$thumbnailUrlFactory = Thumbor\Url\BuilderFactory::construct($server, $secret);

echo $thumbnailUrlFactory
    ->url('http://images.example.com/llamas.jpg')
    ->fitIn(640, 480)
    ->addFilter('fill', 'green');

echo $thumbnailUrlFactory
    ->url('http://images.example.com/butts.png')
    ->crop(20, 20, 300, 300)
    ->valign('middle');

// etc
```
## License

MIT; see [`LICENSE`](LICENSE)
