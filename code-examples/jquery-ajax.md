# Language Examples

## JavaScript (jQuery.ajax)

### Standard language detection (GET):

```javascript
// set endpoint and your access key
var access_key = 'YOUR_ACCESS_KEY';
var query = 'Hello my friend, how are you?';

// AJAX call
$.ajax({
    url: 'http://apilayer.net/api/detect?access_key=' + access_key + '&query=' + encodeURIComponent(query),   
    dataType: 'jsonp',
    success: function(json) {

    // Access and use your preferred validation result objects
    console.log(json.success);
                
    }
});
```

