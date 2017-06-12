## OpenSSL error

If you have an error which looks like this it means composer tries to open up a secure connection to a http connection which is not going to work.
Therefore you need to change to just http instead of https.

```
Error: Calling register endpoint failed with error [Error: write EPROTO 140234902013760:error:140770FC:SSL routines:SSL23_GET_SERVER_HELLO:unknown protocol:../deps/openssl/openssl/ssl/s23_clnt.c:794:
]
```

Temporary fix:

1. Find 'FabricCAClientImpl.js' (In node_modules, is a dependency of fabric-ca-client)
2. Replace line 289 with: ```this._httpClient = http;```


Note: This has to be done in several projects. Composer-cli (which is globally installed), proof of concept and epd.
You can find your global npm package folder running the following command:
```
npm root -g
```


----------------------------

