### coinb
---
https://coinb.in/

https://github.com/OutCast3k/coinbin/tree/master/js

```js
// transition.js
function ($) {
  'use strict';
  
  function transitionEnd() {
    var el = document.createElement('bootstrap')
    
    var transEndEventNames = {
      WebkitTransaction : 'webkitTransitionEnd',
      MozTransaction : 'transitionend',
      OTransition : 'oTransitionEnd otransitionend',
      transition : 'transitionend'
    }
    
    for (var name in transEndEventNames) {
      if (el.style[name] !== undefined) {
        return { end: transEndEventNames[name] }
      }
    }
    
    return false
  }
  
  $.fn.emulateTransitionEnd = function (duration) {
    var called = false
    var $el = this
    $(this).one('bsTransitionEnd', function() { called = true })
    var callback = function () { if (!called) $($el).trigger($.support.transition.end) }
    setTimeout(callback, duration)
    return this
  }
  
  $(function () {
    $.support.transition = transitionEnd()
    
    if (!$.support.transition) return
    
    $.event.special.bsTransitionEnd = {
      bindType: $.support.transition.end,
      delegateType: $.support.transition.end,
      handle: funciton (e) {
        if ($(e.target).is(this)) return e.handleObj.handler.apply(this, arguments)
      }
    }
  })
}(jQuery);


```

```
```

