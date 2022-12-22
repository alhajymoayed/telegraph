---
title: 'Telegraph'
menuTitle: 'Introduction'
description: 'Telegraph is a Laravel package that enables easy Telegram Bots interaction'
position: 1
fullscreen: true
---

<img src="https://banners.beyondco.de/Laravel%20Telegraph.png?theme=light&packageManager=composer+require&packageName=defstudio%2Ftelegraph&pattern=architect&style=style_1&description=Telegram+bots+made+easy&md=1&showWatermark=1&fontSize=100px&images=phone-outgoing" class="light-img" alt=""/>
<img src="https://banners.beyondco.de/Laravel%20Telegraph.png?theme=dark&packageManager=composer+require&packageName=defstudio%2Ftelegraph&pattern=architect&style=style_1&description=Telegram+bots+made+easy&md=1&showWatermark=1&fontSize=100px&images=phone-outgoing" class="dark-img" alt=""/>


<a href="https://packagist.org/packages/defstudio/telegraph" target="_blank">
    <img style="display: inline-block; margin-top: 0.5em; margin-bottom: 0.5em" src="https://img.shields.io/packagist/v/defstudio/telegraph.svg?style=flat&cacheSeconds=3600" alt="Latest Version on Packagist">
</a>

<a href="https://github.com/defstudio/telegraph/actions?query=workflow%3Arun-tests+branch%3Amain" target="_blank">
    <img style="display: inline-block; margin-top: 0.5em; margin-bottom: 0.5em" src="https://img.shields.io/github/actions/workflow/status/defstudio/telegraph/run-tests.yml?branch=main&label=tests&cacheSeconds=3600&logo=data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAABwAAAAcCAMAAABF0y+mAAABiVBMVEUAAAD/iPv9yP3Xm+j/mP//wfVj67Je6bP/h/pVx6p6175d57WQycf+iPn/iPrsnezArd3+t/qpvNJd6LP/jPpu6rv/lPr/kPpc57T/rvtc57Np6rj3oPl37cL/tfn/wv9d6brX//L/g/rYn+n/gvrWm+di6LX+jPrskfGWzMpt6bln4bdd57Jk6LWSycj+vPquwNVo6rde6bP7nvvYnup91b/+vfv/lvtc57OqvNTFs9//t/td57L9t/r/iPpd6LPapej/ovp26bxy67v9lfld6LJr4Ljwsvb/xv3/jv39zv1t6buG5cTDreH5ivlc5rJy676V4cxb57D/y/h50MOy4OCUxcVa77X/iPpe6LP/jP+pu9L8t///tvuQycfArNxp6LzArd151r7/i/9n4bb/j/9e6rT/ifr7ifrskvLYnuhi87tg8blg7bf/vv//lP+wxNtj9b3/qv//oP/+ivz/l/r8ifryn/fvlPTfpPDeofDKtujHtOWX1NF/4seC3cR82sFu7cBo5LiMwPMrAAAAWHRSTlMA/Wv8FAIC/dME/Wj+3tEG/Pv798G1oHRjS0k1LBsWDgsJ/v36+fTy8ezn4+Lh29XNzMzLysLAwLSwr66opJqakY+Ni4J7end0bGlpY11XU048KicmIR8fizl+vwAAAVdJREFUKM9tz2VXAlEQgOFBBURpkE67u7u7E1YFYQl1SbvrlztDiLvss+fc/fCemXMvAEhhKqU759P1rLoxUDUyEh9fPH0z7ALiVrEY+SSNtxNS2upouYv7hOL191aKVsZHUTgbnQPQgDkq4ctHdoQmTWmW4WFzlVUDVpNKXf2fWpWbZIwUq/hcmjWGYnSa1pZZjEoomrEdVAisD7CX6GEb40rqTODxCj21OjDOvjRV8l2jhudBDchg/FUbDIZCITzwQyH6a9+2AMDbm9GfltFnxgAdtQWUgQJl4VQq37uPcSnsfYZzav6Ew18fQ4fUYPM7Qn4uSiIdyx5saJ6T+/3+5KSltshicwI2UpfAKE/aoARTvnn7KMYMdlAUyWRSyHN2JeU42HlCi4TszTHcmuj3iMVdP5JzoyAWNzi6T3ZGrMFCliK3BAqRSC/B2+6IxvYYNcO+2Npfv+yFi10LfBUAAAAASUVORK5CYII=" alt="Tests">
</a>

<a href="https://github.com/defstudio/telegraph/actions?query=workflow%3Alint+branch%3Amain" target="_blank">
    <img style="display: inline-block; margin-top: 0.5em; margin-bottom: 0.5em" src="https://img.shields.io/github/actions/workflow/status/defstudio/telegraph/php-cs-fixer.yml?branch=main&label=code%20style&cacheSeconds=3600" alt="Code Style">
</a>

<a href="https://github.com/defstudio/telegraph/actions?query=workflow%3Aphpstan+branch%3Amain" target="_blank">
    <img style="display: inline-block; margin-top: 0.5em; margin-bottom: 0.5em" src="https://img.shields.io/github/actions/workflow/status/defstudio/telegraph/phpstan.yml?branch=main&label=phpstan&cacheSeconds=3600" alt="Static Analysis">
</a>

<a href="https://packagist.org/packages/defstudio/telegraph" target="_blank">
    <img style="display: inline-block; margin-top: 0.5em; margin-bottom: 0.5em" src="https://img.shields.io/packagist/dt/defstudio/telegraph.svg?style=flat&cacheSeconds=3600" alt="Total Downloads">
</a>

<a href="https://packagist.org/packages/defstudio/telegraph" target="_blank">
    <img style="display: inline-block; margin-top: 0.5em; margin-bottom: 0.5em" src="https://img.shields.io/packagist/l/defstudio/telegraph?style=flat&cacheSeconds=3600" alt="License">
</a>


#### Telegraph is a Laravel package for fluently interacting with Telegram Bots made by 

```php
Telegraph::message('hello world')
    ->keyboard(Keyboard::make()->buttons([
            Button::make('Delete')->action('delete')->param('id', '42'),
            Button::make('open')->url('https://test.it'),
    ]))->send();
```

Get the full source code at [https://github.com/defstudio/telegraph](https://github.com/defstudio/telegraph)


This package is powered by [def:studio](https://github.com/defstudio), follow us on [Twitter](https://twitter.com/FabioIvona)
