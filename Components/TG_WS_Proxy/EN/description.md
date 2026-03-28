**A local SOCKS5 proxy** for Telegram Desktop that speeds up Telegram by redirecting traffic through WebSocket connections. Data is transmitted in the same encrypted format, and no third-party servers are required.

# How it works
```
Telegram Desktop → SOCKS5 (127.0.0.1:1080) → TG WS Proxy → WSS → Telegram DC
```

1. The application sets up a local SOCKS5 proxy on 127.0.0.1:1080
2. Intercepts connections to Telegram IP addresses
3. Extracts the DC ID from the MTProto obfuscation init packet
4. Establishes a WebSocket (TLS) connection to the corresponding DC via Telegram domains
5. If the WS is unavailable (302 redirect), it automatically switches to a direct TCP connection