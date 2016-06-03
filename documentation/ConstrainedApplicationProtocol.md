Constrained Application Protocol
==
> The Web of Things Protocol

> Constrained Application Protocol (CoAP) is a software protocol intended to be used in very simple electronics devices that allows them to communicate interactively over the Internet. It is particularly targeted for small low power sensors, switches, valves and similar components that need to be controlled or supervised remotely, through standard Internet networks ... *From Wikipedia, the free encyclopedia*

>CoAp has a request/response model protocol, clients can make GET, PUT, POST and DELETE requests to resources. Please notice that CoAp does not have SSL/TLS ecryption isn't available over UDP, CoAP makes use of DTLS (Datagram Transport Layer Security). The default level of encryption is equivalent to a 3,072-bit RSA key. Also, CoAp lacks of a publish-subscribe message queue.

- [Eclipse CoAP](http://iot.eclipse.org/getting-started#tutorials)
- [Npm Iopa-Coap](https://www.npmjs.com/package/iopa-coap)
- [Npm Coap](https://www.npmjs.com/package/coap)
- [Constrained Application Protocol (CoAP)](http://tools.ietf.org/html/draft-ietf-core-coap-18)
- [Firefox Copper Cu](https://addons.mozilla.org/en-US/firefox/addon/copper-270430/)
- [Working with bottlenecks: CoAP and MQTT](http://learninginternetofthings.com/bottlenecks-coap-mqtt/)
- [Youtube ARM Constrained Application Protocol (CoAP) Tutorial](https://youtu.be/4bSr5x5gKvA?list=PLgyFKd2HIZlZNsrWXyE4kgLDo_tyLpvDW)

```sh
root@edison:~# npm install coap
-\|/-\|/-\|/--\|/-\|/-\|/-\|-\|/-\|/-\|/-\|-\|/-\|/-\|/-\|/coap@0.15.0 node_modules/coap
��├��─��─ capitalize@1.0.0
��├��─��─ bl@1.0.3
��├��─��─ coap-packet@0.1.13
��├��─��─ debug@2.2.0 (ms@0.7.1)
��├��─��─ lru-cache@4.0.1 (pseudomap@1.0.2, yallist@2.0.0)
��├��─��─ fastseries@1.7.2 (xtend@4.0.1, reusify@1.0.1)
��└��─��─ readable-stream@2.0.6 (process-nextick-args@1.0.6, inherits@2.0.1, util-deprecate@1.0.2, str)
root@edison:~# 
```

```sh
root@edison:~# pip install aiocoap
Downloading/unpacking aiocoap
Installing collected packages: aiocoap
Successfully installed aiocoap
Cleaning up...
root@edison:~# 
```

## Copper CU

[Firefox Copper Cu](https://addons.mozilla.org/en-US/firefox/addon/copper-270430/)