# <image-carousel> polymer 2.0 element

## Install the Polymer-CLI

First, make sure you have the [Polymer CLI](https://www.npmjs.com/package/polymer-cli) installed. Then run `polymer serve` to serve your element locally.


## Clone  it
git clone https://github.com/PaulMatencio/image-carousel

## Viewing Your Element

```
cd image-carousel
$ bower install  ( to install the dependencies )
$ polymer serve  --open  ( to view the demo)
```

## Running Tests

```
$ polymer test ( not yet)
```

Your application is already set up to be tested via [web-component-tester](https://github.com/Polymer/web-component-tester). Run `polymer test` to run your application's test suite locally.

## &lt;image-carousel&gt;

image-carousel is an image carousel. It is based on the Plymerlabs https://github.com/PolymerLabs/polymer-2-carousel

## Properties

  * timer       Number.  scrolling interval timer. Default 1000 ms
  * maxtimer    Number.  Maximum interval. Default 10000ms
  * autoscroll  Boolean. auto-scrolling. Default false
  * title       String
  * label       String
  * appendimage Boolean.  Append image to the carousel. Default is false
  * transition  Boolean. Scrolling with transition. Default false

## API

#### Public methods

  * next_image()
  * previous_image()
  * first_image()
  * last_image()
  * increase_timer()
  * decrease_timer()
  * appendImages()   Must be provided if property appendimage is true repace the _appendImages() private  method


#### Private methods
_autoScroll()   Start/stop auto-scrolling
_fetchImages()  Prefetch images using the fetch API. images are fetched  according to its data-src attribute then update the data-src into src:blob one it is fetched
_appendImages() Append new images. Create a <img> element with  data-src, data-index and  data-image attributes then append it to the carousel dynamically


##Example:

```html
<head>
  <meta charset="utf-8">
  <meta name="viewport" content="width=device-width, minimum-scale=1, initial-scale=1, user-scalable=yes">

  <title>image-carousel demo</title>
  <script src="../../webcomponentsjs/webcomponents-lite.js"></script>
  <link rel="import" href="../image-carousel-custom-styles.html">
  <custom-style>
    <style is="custom-style" include="image-carousel-custom-styles"></style>
  </custom-style>
  <link rel="stylesheet" href="../image-carousel-styles.css">
  <link rel="import" href="../../polymer/lib/elements/dom-repeat.html">
  <link rel="import" href="../image-carousel.html">
</head>
<body>
  <image-carousel timer=500 maxtime=15000  autoscroll$=autoscroll title="" >
    <img data-src="https://app-layout-assets.appspot.com/assets/bg1.jpg" data-image="bg1.jpg" data-index="0">
    <img data-src="https://app-layout-assets.appspot.com/assets/bg2.jpg" data-image="bg2.jpg" data-index="1">
    <img data-src="https://app-layout-assets.appspot.com/assets/bg3.jpg" data-image="bg3.jpg" data-index="2">
    <img data-src="https://app-layout-assets.appspot.com/assets/bg4.jpg"  data-image="bg4.jpg" data-index="3">
    <img data-src="https://app-layout-assets.appspot.com/assets/bg1.jpg" data-image="bg1.jpg" data-index="4">
    <img data-src="https://app-layout-assets.appspot.com/assets/bg2.jpg" data-image="bg2.jpg" data-index="5">
    <img data-src="https://app-layout-assets.appspot.com/assets/bg3.jpg" data-image="bg3.jpg" data-index="6">
    <img data-src="https://app-layout-assets.appspot.com/assets/bg4.jpg"  data-image="bg4.jpg" data-index="7">
 </image-carousel>

<script>
    /* move autosrolling inside my-mixin.html    */
  const carousel = document.querySelector('image-carousel');
  setInterval(_ => carousel.next_image(), 1000);


</script>
</body>
```
