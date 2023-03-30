# JavaScript

## Scenario 1: Ways to call HTTP APIs

#### 1. XMLHttpRequest
```javascript
var Http = new XMLHttpRequest();
var url = 'your-url';
Http.open("POST", url);
Http.send();
```

#### 2. Ajax
```javascript
var settings = 
{
    "url": 'your-url',
	"method": "POST",
	"timeout": 0,
};

$.ajax(settings).done(function (response) {});
```