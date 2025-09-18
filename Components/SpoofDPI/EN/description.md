A simple and fast software designed to bypass **Deep Packet Inspection.**

## How it works
### HTTP

Since most websites in the world now support HTTPS, SpoofDPI doesn't bypass Deep Packet Inspections for HTTP requests, However, it still serves proxy connection for all HTTP requests.

### HTTPS

Although TLS encrypts every handshake process, the domain names are still shown as plaintext in the Client hello packet. In other words, when someone else looks on the packet, they can easily guess where the packet is headed to. The domain name can offer significant information while DPI is being processed, and we can actually see that the connection is blocked right after sending Client hello packet. I had tried some ways to bypass this and found out that it seemed like only the first chunk gets inspected when we send the Client hello packet split into chunks. What SpoofDPI does to bypass this is to send the first 1 byte of a request to the server, and then send the rest.