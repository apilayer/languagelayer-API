# Language Examples

## PHP (CURL)

### Standard language detection in PHP (GET):

```php
// set API Access Key
$access_key = 'YOUR_ACCESS_KEY';

// set query text
$query = 'Hello my friend, how are you today?';

// Initialize CURL:
$ch = curl_init('http://apilayer.net/api/detect?access_key='.$access_key.'&query='.$query.'');  
curl_setopt($ch, CURLOPT_RETURNTRANSFER, true);

// Store the data:
$json = curl_exec($ch);
curl_close($ch);

// Decode JSON response and store array:
$detection_result = json_decode($json, true);
```

### Batch language detection in PHP (POST):

```php
function languagelayer_batch($query_array) {

  // set access key
  $access_key = 'YOUR_ACCESS_KEY';

  
  foreach($query_array as $value) { $fields_string .= 'query[]='.$value.'&'; }
  rtrim($fields_string, '&');

  // Initialize CURL:
  $ch = curl_init('http://apilayer.net/api/batch?access_key='.$access_key);  
  curl_setopt($ch, CURLOPT_RETURNTRANSFER, true);
  curl_setopt($ch, CURLOPT_POST, true);
  curl_setopt($ch, CURLOPT_POSTFIELDS, $fields_string);
  curl_setopt($ch, CURLOPT_RETURNTRANSFER, 1);

  // Store the data:
  $json = curl_exec($ch);
  curl_close($ch);
  
  echo $json;

  // Decode JSON response:
  $detection_results = json_decode($json, true);

  // Access and use your preferred validation result objects
  return $detection_results;

}

// set query texts
$query_array = array('hey friend', 'hola amigo', 'hallo freund');

// store results array
$results_array = languagelayer_batch($query_array);
```
