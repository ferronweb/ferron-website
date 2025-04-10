---
title: Automatic TLS
---

Ferron supports automatic TLS (v0.7.0 and newer) via Let's Encrypt and TLS-ALPN-01 ACME challenge. The domain names for the certificate will be extracted from the host configuration (wildcard domains are ignored, since TLS-ALPN-01 ACME challenge doesn't support them). The automatic TLS will work when the HTTPS port is set to `443`.

The automatic TLS functionality is used to obtain TLS certificates automatically, without needing to manually import TLS certificates or use an external tool to obtain TLS certificates, like Certbot. This makes the process of obtaining TLS certificate more convenient and efficient.

Ferron supports both production and staging Let's Encrypt directories. The staging Let's Encrypt directory can be used for testing purposes and to verify that the server and automatic TLS is configured correctly.

Below is the example Ferron configuration that enables automatic TLS using production Let's Encrypt directory:

```yaml
global:
  secure: true
  enableHTTP2: true # Enable HTTP/2 for improved performance
  enableAutomaticTLS: true
  automaticTLSContactEmail: "someone@example.com" # Replace "someone@example.com" with actual email address
  automaticTLSContactCacheDirectory: "/path/to/letsencrypt-cache" # Replace "/path/to/letsencrypt-cache" with actual cache directory. Optional property, but recommended
  automaticTLSLetsEncryptProduction: true

hosts:
  - domain: "example.com" # Replace "example.com" with your website's domain name
    wwwroot: "/var/www/html"
```
