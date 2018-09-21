# Web Console

## Paste in Web Console

### Insert snippet in browser console

* Copy the console URL and paste it to a new window
* Open Developer Tools then click Console tab
* Paste this code

```javascript

var sendString = (function(rfb, force, sendDelay) { 
sendDelay = sendDelay || 25;
var _q = [];
var _qStart = function() {
var chr = _q.shift();
if (chr) {
  rfb.sendKey(chr);
  setTimeout(_qStart, sendDelay);
}
};
var _qStop = function() { _q.length = 0; };
var fn = function sendString(str) {
_qStop();
str = str || '';
var chr;
for (var i=0; i < str.length; i++) {
  chr = str[i].charCodeAt();
  _q.push(chr);
}
_qStart();
};
if (rfb.sendString && true !== force) {
console.warn('rfb.sendString not installed because it already exists.  Use force if you\'d like');
}
else {
rfb.sendString = fn;
}
return fn;
})(rfb);

```

* On the same console type `sendString("Commandline to be pasted in the console")`

### Install Chrome Extension

[https://chrome.google.com/webstore/detail/digital-ocean-paste-in-co/pigihfibffjpekhnjeofgbdkppghbofk](https://chrome.google.com/webstore/detail/digital-ocean-paste-in-co/pigihfibffjpekhnjeofgbdkppghbofk)

## Reference

* [https://www.digitalocean.com/community/questions/copy-and-paste-into-console](https://www.digitalocean.com/community/questions/copy-and-paste-into-console)