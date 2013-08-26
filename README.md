## Terry-Mao/gopush

`Terry-Mao/gopush` is an push server written by golang. (redis + websocket)

## Requeriments
regisgo and golang websocket is needed.
```sh
# all platform
# redis
$ go get github.com/garyburd/redigo
# websocket
$ go get code.google.com/p/go.net/websocket 
```

## Installation
Just pull `Terry-Mao/gopush` from github using `go get`:

```sh
$ go get github.com/Terry-Mao/gopush
```

## Usage
```sh
# start the gopush server
$ ./gopush -c ./gopush.conf

# open http://localhost:8080/client in browser and press the Send button

# connect to your redis
$ redis-cli 
$ redis > PUBLISH youKey "message"

# then your browser will alert the "message"
```

## Protocol
Subscribers use `websocket` connect to the `gopush` then write a `sub key` to
the server and it will receive a json response when someone publish a message 
to the key in your `redis`.

response json field:
# ret
* 0 : ok
* 65535 : internal error
* 1 : authentication error
# msg
* error message
# data

ret:
* 0 : ok
* 65535 : internal error
* 1 : authentication error

msg:
* error message

data:
>>>>>>> 95a1f49a0d2f9244b67e10a3f2ec3a72e20ae194
* the publish message

the reponse json examples:
```json
{
    "ret" : 0,
    "msg" : "ok",
    "data" : "message"
}
```

## Documentation
Read the `Terry-Mao/gopush` documentation from a terminal

```sh
$ go doc github.com/Terry-Mao/gopush
```

Alternatively, you can [gopush](http://go.pkgdoc.org/github.com/Terry-Mao/gopush).
