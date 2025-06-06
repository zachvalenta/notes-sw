# ⛩️

## 参考

🔍 https://networkengineering.stackexchange.com/
📹 https://www.youtube.com/watch?v=qiQR5rTSshw https://www.youtube.com/watch?v=3QhU9jd03a0
📚
* https://intronetworks.cs.luc.edu/
* Kozierok tcp-ip guide
* Ross network know-how

## 进步

# 🏠 HOME INTERNET

📚
* Kranz cybersecurity https://www.manning.com/books/making-sense-of-cybersecurity

> I need to set up home internet. I've never done this before. I have a software engineering background, so I'm decently familiar with networking in the form of HTTP and to a lesser degree DNS, but spend little time thinking about TCP/IP or the link layer of the stack.

OVERVIEW
* https://claude.ai/chat/61b526aa-9b0e-4753-b6f3-8c6d690f4887
* https://chatgpt.com/c/6793916a-f74c-8004-9862-40371d3c5764
* https://dailywireless.org/internet/what-is-mbps/

WIFI
* https://hpbn.co/introduction-to-wireless-networks/
* https://hpbn.co/wifi/

MOBILE
* https://hpbn.co/mobile-networks/
* https://hpbn.co/optimizing-for-mobile-networks/

LAG VS. LATENCY
* https://chatgpt.com/c/67858c31-3768-8004-bf51-e414c9a29c6b
* https://livebook.manning.com/book/latency/chapter-1/v-5/12

LINKS
* https://www.youtube.com/watch?v=5qOvNbDzwUI
* https://www.youtube.com/watch?v=OKXc3GRHVkg&lc=UgzklVU-UvccTzvthxx4AaABAg

## ISP

ENTRY POINTS
* _cable_: coaxial port
* _fiber_: optical network terminal (ONT)
* _DSL_: phone jack (e.g. rj11)

---

BYO https://arstechnica.com/tech-policy/2022/08/man-who-built-isp-instead-of-paying-comcast-50k-expands-to-hundreds-of-homes/
* Connection type (fiber/cable/DSL)

ALTERNATIVE APPROACHES
* Mobile hotspot/tethering (for temporary or light use)
* Satellite (Starlink for rural areas)
* Fixed wireless (5G home internet)

- Check local ISPs: Fiber > Cable > DSL
- Compare: speed, price, data caps, contract length
- Verify actual speeds for your address

Research ISPs (Internet Service Providers) available locally. Common ones include cable (e.g., Comcast), fiber (e.g., AT&T Fiber, Verizon Fios), DSL, or satellite (if rural).

Check download/upload speeds. For software engineers:
50 Mbps+ is good for general use and light remote work.
100 Mbps+ is recommended for heavy downloading, video calls, or multiple users.
Look for symmetric speeds (equal upload/download) if you upload large files.

## hardware

MODEM
* _modem_: converts ISP signal (cable, fiber, dsl) into data
* operation: ISP line into modem input port
* models: Motorola MB8600
> need ISP compatibility

ROUTER
* _router_: handles wifi and manages devices on your home network
* operation: Ethernet cable from modem output (marked LAN|Ethernet) to routers WAN port
* setup: login via browser using default creds and IP [192.168.1.1], create SSID [wifi name] and replace default pw

---

ROUTER
* dual-band (2.4 ghz + 5 ghz) or tri-band for modern devices.
* wi-fi 6 (802.11ax) for better speed and efficiency.
* example: tp-link archer ax73, asus rt-ax86u.

- Key specs: WiFi 6, dual-band, gigabit ports

## speed

🛠️ https://fast.com/ https://www.speedtest.net/

---

* 115/4.5 at Wilmington apartment
> 搜 'internet speed test'
* https://news.ycombinator.com/item?id=26343394
* https://news.ycombinator.com/item?id=31062799
* https://www.lambdafunctions.com/articles/make-internet-connection-worse
* https://danluu.com/octopress-speedup/
* https://news.ycombinator.com/item?id=24478149
* https://dailywireless.org/internet/what-is-mbps/
```sh
# https://weiyen.net/articles/useful-macos-cmd-line-utilities
networkQuality
networksetup
```

MONITORING/DEBUGGING
* Speed tests from multiple devices
* Check router logs
* `ping`/`traceroute` for connectivity issues
* WiFi analyzer for channel congestion

## config

---

QoS (Quality of Service)
* Prioritize video calls/gaming
* Limit bandwidth hogs
* Port forwarding if needed

IP Range (DHCP)
* Default: 192.168.1.x
* Consider separate ranges for IoT/guests
* Reserve IPs for printers/NAS

DNS
* ISP default vs alternatives (1.1.1.1, 8.8.8.8)
* Local DNS for custom domains/pihole

Security
* WPA3 for wifi
* Guest network isolation
* MAC filtering (optional)
* VLANs (if supported)

Networking Tips for Engineers
* Port Forwarding: Configure for self-hosted services or development needs.
* Static IPs: Set static IPs for devices like servers or NAS on your local network.
* VLANs: Use if you want to segment traffic (e.g., IoT vs. work devices).
* Monitoring: Tools like Pi-hole (for DNS-level ad blocking) or router logs to monitor traffic.

# 🟨️ ZA

* _network partition_: when two nodes can no longer talk i.e. nodes within a db cluster
* find wifi speeds for geographies https://news.ycombinator.com/item?id=24478149

* _network discovery_: figure out what's running on your network https://softwareengineeringdaily.com/2021/01/14/network-discovery-with-hd-moore/

topologies
* _bus_: everything in a row w/ shared cable as medium; one node dropping won't affect others
* _ring_: dropped node breaks entire ring (unlike bus)
* _star_: clients in a ring around server (usually a switch)
* _root_: server node with clients node extending downwards; easier to work on branches in isolation
* _mesh_: all nodes connnected to all others

---

* undersea cables get snapped all the time? https://news.ycombinator.com/item?id=42176496 https://www.submarinecablemap.com/

* _layer 1_: electrical engineering, wires, frequencies 
* _data link_: physical medium for transmission of signal btw nodes [NKH 30]
* _materials_: radiowaves over air, light over glass (fiberoptic; lowest signal loss) electricity over copper (Ethernet; degrades over even short distances; DSL is copper wires from ISP) https://www.youtube.com/watch?v=lUo45NqPyq8 https://www.youtube.com/watch?v=XaGXPObx2Gs
* radio SDR https://nostarch.com/practical-sdr

* _bridge_: connect n networks
* _MAC address_: way to address NIC, not whole device https://gkbrk.com/2018/12/free-hotel-wifi-with-python-and-selenium/ https://jvns.ca/blog/2013/10/29/day-18-in-ur-connection/
* _network inferface_: https://jvns.ca/blog/2017/09/03/network-interfaces/
* _out-of-band interface_: robot that can physically manipulate server (something wrong w/ RAID array)

## data centers

https://news.ycombinator.com/item?id=42743019
https://danluu.com/datacenter-power/

semantics
* _placement_: determine ability to provision based on cpu/mem/storage
* _provision_: allocate existing cpu/mem/storage to asset
* _rightsize_: align provisioned w/ usage https://softwareengineeringdaily.com/2021/01/12/kubecost-with-webb-brown/
* _cmdb_: db of provisioned https://tumblr.github.io/collins/ Turbonomic fills similar role
* _build_: probably installing ESXi onto server blades somewhere

assets
* _asset_: generic term for infra (plant, az, cluster, etc.)
* _server_: vm in cluster
* _cluster_: n vms in pod
* _pod_: hw rack
* _az_: grouping in plant
* _plant_: all az

metrics
* usage
* peak
* p90

misc
* hierarchy: server, cluster, pod, plant
* data center vendors: Equinix, CoreSite, and Digital Realty Trust
* _UCS_: Cisco data center server mgmt e.g. you have UCS to manage a bunch of UCS (Cisco) servers
* _Pure Storage_: flash for UCS server
* _Netflow_: Cisco protocol to export traffic data from their devices [Network Flow Analysis] there's also something called 'sflow'
* _Redfish_: API to manage DMTF servers
* _DMTF_: consortium (Dell, Lenovo)

## hardware

* _repeater_: take in signal, interprets data, generates new clean signal, outputs signal; fights attentuation (degradation of signal over distance); half-duplex
* _hub_: same as repeater but outputs to multiple ports aka 'multiple port repeater'; allowed transition from hub topology to star
* _switch_: handle data inside your network; connects devices; uses MAC addr to map to node which listens on specific port which, combined with buffers to store data, allows for full duplex; the amount of traffic today demands full duplex
* just a chip https://news.ycombinator.com/item?id=40694254
* _router_: connect networks e.g. LAN to WAN [Cisco Routers for the Desperate 2.11]
* _default gateway_: IP address of router
* _modem_: connect to ISP's WAN (via coax cable) 🗄 `netgear-modem.zip`

## telephony

📙 Gleick ch. 6

* _toner_: tone generator|signal used for testing/troubleshooting telephone lines|circuits; often part of a toolset called a tone and probe kit, which is used by technicians to locate and identify cables or wires

---

* open RAN, architecture in general https://www.youtube.com/watch?v=-fVHO_WCGF8
* PSTN https://news.ycombinator.com/item?id=27602383
* packet switched (internet: non-deterministic) vs. circuit switched (analog telephony: dedicated connection per call)
* on 4G calls are just data (vs. 3G, where they are circuit switched) https://stratechery.com/2020/india-jio-and-the-four-internets
* _physical_: backbone (Tata, Telia Carrier) last mile (Comcast, Cox) https://medium.freecodecamp.org/inside-the-invisible-war-for-the-open-internet-dd31a29a3f08#.65152gd3x

__stingray__: cell tower simulator used to grab phone location (vs. open warrant to search)

https://scottbot.net/the-route-of-a-text-message/

* phone location data https://motherboard.vice.com/en_us/article/nepxbz/i-gave-a-bounty-hunter-300-dollars-located-phone-microbilt-zumigo-tmobile

https://www.ben-evans.com/benedictevans/2019/1/16/5g-if-you-build-it-we-will-fill-it

📍 check out info on speaker from HOPE

fiberoptic https://www.wsj.com/articles/google-plans-fiber-optic-network-to-connect-via-saudi-arabia-and-israel-for-first-time-11606143590

wall jack - demarc point for house - telephone wire - central office - use North American Dialing Plan (routing for central offices) allows central offices to talk to one another

[diff btw PSTN and DSL](https://networkengineering.stackexchange.com/a/46112/40008)

* _SS7_: PSTN protocol

https://motherboard.vice.com/en_us/article/mbzvxv/criminals-hackers-ss7-uk-banks-metro-bank

companies offering "track this cell phone anywhere on the planet" aaS

> The underlying issue with SS7, however, is that the network believes whatever you tell it: anyone with access to the SS7 network can send a message, and the network may not check where the message is coming from, or whether a legitimate telecoms company sent it. - https://www.thedailybeast.com/the-companies-that-will-track-any-phone-on-the-planet

> SS7, invented in 1975, is still the protocol that allows telephone networks all over the world to talk to one another. It was built on the assumption that anyone who can connect to the network is a trusted network operator. When it was created, there were only 10 companies using SS7. - https://www.nytimes.com/2018/12/26/opinion/cellphones-security-spying.html

> Another protocol, GSM, invented in 1991, allows your cellphone to communicate with a cell tower to make and receive calls and transmit data. The older generation of GSM, known as 2G, doesn’t verify that the tower that your phone connects to is authentic, making it easy for anyone to use a cell-site simulator and impersonate a cell tower to obtain your location or eavesdrop on your communications...later generations of GSM such as 3G, 4G and 5G solve many of its problems. Yet our phones all still support 2G and most have no way to disable it, making them susceptible to attacks. What’s more, research has shown that 3G, 4G, and even 5G have vulnerabilities that may allow new generations of cell-site simulators to continue working. - https://www.nytimes.com/2018/12/26/opinion/cellphones-security-spying.html

https://theintercept.com/2018/06/25/att-internet-nsa-spy-hubs/

While network operators would usually prefer to send data through their own networks, often a more direct and cost-efficient path is provided by other providers’ infrastructure. If one network in a specific area of the country is overloaded with data traffic, another operator with capacity to spare can sell or exchange bandwidth, reducing the strain on the congested region. This exchange of traffic is called “peering” and is an essential feature of the internet.

The data exchange between AT&T and other networks initially takes place outside AT&T’s control, sources said, at third-party data centers that are owned and operated by companies such as California’s Equinix.

As of March 2018, some 197 petabytes of data – the equivalent of more than 49 trillion pages of text, or 60 billion average-sized mp3 files – traveled across its networks every business day.

Under a Ronald Reagan-era presidential directive – Executive Order 12333 – the NSA has what it calls “transit authority,” which it says enables it to eavesdrop on “communications which originate and terminate in foreign countries, but traverse U.S. territory.” That could include, for example, an email sent by a person in France to a person in Mexico, which on its way to its destination was routed through a server in California. According to the NSA’s documents, it was using AT&T’s networks as of March 2013 to gather some 60 million foreign-to-foreign emails every day, 1.8 billion per month.

Without an individualized court order, it is illegal for the NSA to spy on communications that are wholly domestic, such as emails sent back and forth between two Americans living in Texas. However, in the aftermath of the 9/11 attacks, the agency began eavesdropping on Americans’ international calls and emails that were passing between the U.S. and other countries. That practice was exposed by the New York Times in 2005 and triggered what became known as the “warrantless wiretapping” scandal.

In 2008, Congress weighed into the dispute and controversially authorized elements of the warrantless wiretapping program by enacting Section 702 of the Foreign Intelligence and Surveillance Act, or FISA.

 A classified 2012 memo describes the agency’s efforts to use IP addresses to home in on internet data passing between the U.S. and particular “regions of interest,” including Iran, Afghanistan, Israel, Nigeria, Pakistan, Yemen, Sudan, Tunisia, Libya, and Egypt. But this process is not an exact science, as people can use privacy or anonymity tools to change or spoof their IP addresses. A person in Israel could use privacy software to masquerade as if they were accessing the internet in the U.S. Likewise, an internet user in the U.S. could make it appear as if they were online in Israel. It is unclear how effective the NSA’s systems are at detecting such anomalies.

A top-secret NSA memo about the court’s ruling, which has not been disclosed before, explained that the agency was collecting people’s messages en masse if a single one were found to contain a “selector” – like an email address or phone number – that featured on a target list.

“One example of this is when a user of a webmail service accesses her inbox; if the inbox contains one email message that contains an NSA tasked selector, NSA will acquire a copy of the entire inbox, not just the individual email message that contains the tasked selector,” the memo stated.

Today, the facility contains six large V-16 yellow Caterpillar generators that can provide backup electricity in the event of a power failure, according to the Chicago Sun Times. Inside the skyscraper, AT&T stores some 200,000 gallons of diesel fuel, enough to run the generators for 40 days.

Saunders also claimed that, had Bush been in Manhattan during the 9/11 attacks, the Secret Service would have taken him to safety inside the AT&T facility. “It’s the strongest building in town,” he said.

“By cutting into the peering links, they get not only AT&T’s data, they get all the data that’s interchanged between AT&T’s network and other companies,” Klein told The Intercept in a recent interview.

In 2011, CenturyLink acquired Qwest as part of a $12.2 billion merger deal.

Twenty-five miles north of Seattle, there is a major intercontinental undersea cable called Pacific Crossing-1 https://www.submarinecablemap.com/

## transmissions

types
* _simplex_: one-way communication
* _unicast_: simplex + one recipient e.g. TCP
* _multicast_: simplex + n recipients; aka syndication https://signalsandthreads.com/multicast-and-the-markets/
* _broadcast_: simplex + all recipients
* _duplex_: two-way communication
* _half duplex_: non-simultaneous e.g. walkie talkie
* _full duplex_: simultaneous e.g. phone

za
* _control_: filter; requires routing table
* _forwarding_: msg pass through proxy
* _port forwarding_: forward from local ports to remote https://hacker-tools.github.io/remote-machines/
* _out-of-band (OOB)_: communication outside normal channel e.g. getting phone call from a website
* _out-of-band management_: use interface on server to manage it
* _in-band management_: use SSH; can't fix problems w/ boot or access firmware https://en.wikipedia.org/wiki/Out-of-band_management
* _SNMP_: Simple Network Mgmt; used for out-of-band
