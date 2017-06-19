The client is the agent that runs on machines to grab network data. 

The core library used here is libpcap/winpcap, which - in promiscuous mode - can capture packets received by the operating system. Promiscuous mode is crucial, since we need to be able to capture layer 2 packets (ok, technically "frames", but whatever) and keep them.

The two main protocols that the client looks for are LLDP and CDP. There are a few other discovery protocols that I would love to be able to play with and work into the client, but in lieu of these existing (and LLDP being vendor-agnostic), I'll settle for just these two. These protocols contain similar data, formatted slightly differently, that can be extracted to provide useful information such as:

Switch IP
Switch name
Switch MAC address
VLAN
Device capabilities
And various other things.

Normally these protocols are ignored by most OSes and are just used by inter-connecting networking devices to build a picture of the network topology. Well, given that that data is often present on the wire, it can be grabbed and interpetted as text data. 

Useful resources have been:


Its important to note that not all switches will have LLDP and CDP advertisements enabled. If you haven't got access to your network infrastructure and these aren't enabled, this client is kind of useless to you, unfortunately!