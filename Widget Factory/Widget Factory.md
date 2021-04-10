

# Widget Factory

[Widget Factory | jQuery Learning Center](https://learn.jquery.com/jquery-ui/widget-factory/)



通常是用 $.extend 來撰寫，傳入參數與預設值的合併...

```javascript
// Setting Options on Initialization

$.fn.plugin = function( options ) {
    options = $.extend( {}, $.fn.plugin.defaults, options );
    console.log(options)
};
 
$.fn.plugin.defaults = {
    param1: "foo",
    param2: "bar",
    param3: "baz"
};

$.fn.plugin()
// {param1: "foo", param2: "bar", param3: "baz"}


$.fn.plugin({param1:123})
// {param1: 123, param2: "bar", param3: "baz"}

```



Now, Use the Widget Factory...

```javascript
// --- Now, Use the Widget Factory ---

$.widget( "ns.plugin", {
 
    // Default options.
    options: {
        param1: "foo",
        param2: "bar",
        param3: "baz"
    },
    _create: function() {
    	// 小部件工廠為我們提供了兩個屬性
        console.log(this.options);
        console.log(this.element);
    },
    // Create a public method.
    GetOptions: function(param) {
    	return this._doSomething(param);
    },

    // Create a private method.
    _doSomething: function(param) {
        return param + ' is '+ this.options[param];
    }
 
});

var p = $.ns.plugin({param1: 123});
console.log(p.GetOptions('param1'));
// param1 is 123

console.log(p.GetOptions('param2'));
// param2 is bar
```

































