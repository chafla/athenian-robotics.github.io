# MQTT Notes

## MQTT Broker Installation

### OSX

To install mosquitto:
```bash
$ brew install mosquitto
```

To add mosquitto to launchd:
```bash
$ brew services start mosquitto
```

If you don't want to run mosquitto as a background service:
```bash
$ /usr/local/sbin/mosquitto -c /usr/local/etc/mosquitto/mosquitto.conf
```

### Windows

Create a folder named `mosquitto` in `C:\Program Files (x86)`

Download and install [Win32 OpenSSL v.1.0.2j Light](http://slproweb.com/products/Win32OpenSSL.html). Select the option to save the binaries to /bin. Find `libeay32.dll` and `ssleay32.dll`, move them to `mosquitto`.

Download [pthreadVC2.dll](ftp://sources.redhat.com/pub/pthreads-win32/dll-latest/dll/x86/), move it to `mosquitto`.

Download and install [mosquitto](https://mosquitto.org/download/). Leave the

Open Services, find `Mosquitto Broker` and start it.

To be able to run it from the command line, open System Properties, go to the Advanced tab, and open Environment Variables. Add the path to `mosquitto` to the user Path variable, followed by ;.
e.g.
```
C:\Program Files (x86)\mosquitto;
```

Commands are run in cmd like osx/linux.

### Docker

To run mosquitto as a docker service:
```bash
$ docker run -ti -p 1883:1883 -p 9001:9001 toke/mosquitto
```

Image details are [here](https://github.com/toke/docker-mosquitto)

### Raspberry Pi

```bash
$ sudo apt-get install mosquitto
$ sudo apt-get install mosquitto-clients
```

## Testing from CLI

### Subscribe

```bash
$ mosquitto_sub -d -h localhost -t /testnode
Client mosqsub/27524-pleiku.lo sending CONNECT
Client mosqsub/27524-pleiku.lo received CONNACK
Client mosqsub/27524-pleiku.lo sending SUBSCRIBE (Mid: 1, Topic: /testnode, QoS: 0)
Client mosqsub/27524-pleiku.lo received SUBACK
Subscribed (mid: 1): 0
```

### Publish

```bash
$ mosquitto_pub -d -h localhost -m "simple val" -t /testnode
Client mosqpub/27472-pleiku.lo sending CONNECT
Client mosqpub/27472-pleiku.lo received CONNACK
Client mosqpub/27472-pleiku.lo sending PUBLISH (d0, q0, r0, m1, '/testnode', ... (10 bytes))
Client mosqpub/27472-pleiku.lo sending DISCONNECT
```
