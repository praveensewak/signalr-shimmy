# signalr-shimmy
## JavaScript SignalR Client with jQuery shimmied

*Credit where credit is due*: love Pawel's work, heavily borrowed from his `signalr-no-jquery' (infact an exact fork). I just needed a faster turnaround to the issues

jQuery shim borrowed from [react-native-signalR](https://github.com/olofd/react-native-signalr)

This version of signalR client doesn't add jQuery to `window` object but imports jQueryShim locally to signalR and exports `hubConnection`.
jQueryShim file contains only bare-minimum of jQuery to make signalR client run.

This package is not meant to be used with ASP.NET Core version of SignalR

### Usage

```
npm i --save-dev signalr-shimmy
```

#### ES6 Loader

```
import { hubConnection } from 'signalr-shimmy'
```

#### HTML

Use just like regular signalR but without $ namespace

```
let connection = hubConnection('http://[address]:[port]', options)
connection.qs = { 'access_token': 'SECRET_TOKEN' };
const hubProxy = connection.createHubProxy('hubNameString')

// set up event listeners i.e. for incoming "message" event
hubProxy.on('message', function(message) {
    console.log(message)
});

// connect
connection.start({ jsonp: true })
.done(function(){ console.log('Now connected, connection ID=' + connection.id); })
.fail(function(){ console.log('Could not connect'); })
```

### Problems

Feel free to create pull requests and raise issues https://github.com/praveensewak/signalr-shimmy/issues
