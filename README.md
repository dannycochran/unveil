#unveil.js
###A very lightweight plugin to lazy load images for jQuery or Zepto.js

A fork of [Luis Almeida's unveil](http://luis-almeida.github.com/unveil/).


My own version of unveil that allows for more fine tuned control of the image unveiler (you can specifiy a container and start & stop the scroll/resize listeners).

### Example Usage

When rendering a view:


```
var $container = this.$('ol.container'),
    callback = function () {
      var $el = $(this);
      $el.addClass('loading');
      $el.one('load', function () {
        setTimeout(function () { $el.removeClass('loading'); }, 1000);
      });
    };

// instaniate unveiler with 0 threshold,
// a callback for applying an opacity transition,
// and the $container to watch for scroll events
var unveiler = $container.find('img').unveil(0, callback, $container);

// set all your images 'src' attributes to be 'data-src' instead
unveil.replaceDataSrc();

// start listening for scroll and resize events
unveiler.start();

// do an initial unveil
unveiler.unveil();
```

When destroying the view or moving to a new view:

```
unveiler.stop();
```

###License
Unveil is licensed under the [MIT license](http://opensource.org/licenses/MIT).
