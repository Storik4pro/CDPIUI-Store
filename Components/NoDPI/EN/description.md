NoDPI is a utility designed to bypass DPI (Deep Packet Inspection). What is DPI? DPI is a technology for inspecting network packets based on their content to regulate and filter traffic. It is often used by internet service providers to censor and block access to certain web resources and protocols. The goal of this program is to "trick" DPI by modifying network packets, although in reality, this trickery is often simply a consequence of a lack of computing resources and time.

This utility was developed primarily for Russian users as a simpler (but less powerful) replacement for similar tools. In most cases, it gets the job done; in particular, it allows you to use YouTube without any problems.

But unfortunately, the absolute performance of this utility cannot be guaranteed. Some sites, such as YouTube, are good to unlock, while others, as Instagram.com or Facebook.com, require completely different methods for bypassing locks, which are not yet implemented in this utility from their low-leveling and difficulty. Sometimes, the performance of certain sites can also depend on the provider - how it blocks the site and what technical means applies

## How does this work

NoDPI launches a proxy server on your computer through which you direct http(s) traffic. The program intercepts ClientHello of outing connections and fragments them according to one of the following methods:

*Random fragmentation (by default)*

Clienthello is divided into several parts of random length. Each part is glued with the prefixes of the type of Clienthello and then all this is sent in one package.

*Fragmentation by SNI*

In the package there is a field containing SNI record. ClientHello is divided into 4 parts: to SNI, the first and second half of SNI, and all that is after it. The title indicating the type Clienthello is attached to each part and then all this is sent in one bag.

Also regardless of the method, the TLS version is replaced by version 1.3, which is the most modern (but this does not mean that your data begins to be transmitted according to the specifications of this version). All this together allows you to get around the lock. Apparently DPI does not yet have the necessary capacities to unravel this "ball" and simply ignore such traffic, saving time and effort. But it is possible that soon these methods will not be workers.

### Important
NoDPI only works with HTTPS traffic. He can also take HTTP traffic, but purely for compatibility - sites working through this outdated protocol are practically not subject to unlock and the program simply sends traffic to the addressee.


NoDPI does not collect and does not send any data about you, does not use any third -party programs and libraries, does not interfere in the system processes and does not require administrator rights to work.

The entire NoDPI code is written exclusively on the Python and uses only its standard library.

## Sites currently unavailable via NoDPI
As of October 2025, Instagram and Facebook were not unlockable with NoDPI. Please use [GoodbyeDPI](https://github.com/ValdikSS/GoodbyeDPI) by @ValdikSS. All sites blocked by IP address are also unavailable.