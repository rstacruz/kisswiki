## display filter

- https://wiki.wireshark.org/DisplayFilters
- http://www.thegeekstuff.com/2012/07/wireshark-filter/
- AND: `&&`
- OR: `||`
- filter only http: `http`
- filter http and filter out `protocol==SSDP` and `protocol==TLSV1`: `http && !udp && !ssl`
  - http://serverfault.com/questions/216814/wireshark-display-filter-protocol-tlsv1-and-packetlength
  - http://serverfault.com/questions/686595/how-can-the-ssdp-protocol-be-filtered-out-of-wireshark-view
- domain http://stackoverflow.com/questions/22028943/filtering-by-domain: `http.host contains "wp.pl"`

## Windows

Install npcap

- https://wiki.wireshark.org/CaptureSetup/Loopback
  - https://nmap.org/npcap/
- https://ask.wireshark.org/questions/29211/how-can-wireshark-capture-local-host-traffic-on-windows
