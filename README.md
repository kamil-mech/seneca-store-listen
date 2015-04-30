# seneca-store-listen 0.1.0

Allow offline seneca stores to listen for seneca connections like regular DBs.
Uses seneca-transport.

Install:
```
    npm install seneca-store-listen
```

Currently supports:
- mem-store
- jsonfile-store

Listen feature usage:
- add code below to your app(before you add any plugins with seneca.use)
```
  var sl = require('seneca-store-listen')()

  sl.host(db, function(server_config){
    setTimeout(function(){
      seneca
      .client(server_config)
      .ready(function(){

        seneca = this
        
        // do stuff, e.g.
        seneca.use('some-plugin')
        seneca.make$('something').save$()
        seneca.make$('something').list$()
      })
    }, 2000)
  })
```
- run your app
