A standalone DPI countermeasure that doesn't require connecting to any third-party servers. It can help bypass blocking or slowdowns of HTTP(S) websites, and perform signature analysis of TCP and UDP protocols, for example, to block VPNs.
The project is primarily aimed at low-power embedded devices – routers running OpenWrt. However, most of the functionality is available on Windows.

## How it works

In the simplest case, you're dealing with passive DPI. Passive DPI can read traffic from the stream and can inject its own packets, but it can't block incoming packets. If the request is "bad," passive DPI injects an RST packet, optionally supplementing it with an HTTP redirect packet. If the fake packet is injected only for the client, then iptables commands can be used to drop the RST and/or redirect to a stub based on specific conditions, which need to be tailored to each provider individually. This is how we bypass the consequences of a ban trigger. If a passive DPI sends an RST packet to the server, among other things, there's nothing you can do about it. Your task is to prevent the ban trigger from being triggered. iptables alone won't do. This project is aimed specifically at preventing the ban from being triggered, not at eliminating its consequences.

An active DPI is inserted into the wire and can drop packets based on any criteria, including recognizing TCP streams and blocking any packets belonging to that stream.

How can you prevent a ban trigger from being triggered? Send something the DPI doesn't expect, something that disrupts its request recognition and blocking algorithm.

Some DPIs cannot recognize an HTTP request if it is split into TCP segments. For example, we send a request like `GET / HTTP/1.1\r\nHost: kinozal.tv......` in two parts: first comes `GET`, then `/ HTTP/1.1\r\nHost: kinozal.tv......`. Other DPI issues arise when the `Host:` header is written in a different case, for example, `host:`. In some cases, adding an extra space after the method: `GET /` → `GET /` or adding a period at the end of the hostname: `Host: kinozal.tv.`

There is also more advanced magic aimed at overcoming DPI at the packet level.

Learn more about DPI:
[https://habr.com/ru/post/335436](https://habr.com/ru/post/335436) or [https://web.archive.org/web/20230331233644/https://habr.com/ru/post/335436/](https://web.archive.org/web/20230331233644/https://habr.com/ru/post/335436/)
[https://geneva.cs.umd.edu/papers/geneva_ccs19.pdf](https://geneva.cs.umd.edu/papers/geneva_ccs19.pdf)