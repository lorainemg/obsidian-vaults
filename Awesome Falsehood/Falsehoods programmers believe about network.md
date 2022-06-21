# Falsehoods programmers believe about network
Creado: 2022-06-21 17:07
Tags: #every-programmer-should-know, #falsehoods, #network
Topic: [[Awesome Falsehood]] 

----

- Data on the network cannot be altered.
- Encrypted data on the network cannot be altered.
- Data cannot be accidentally corrupted, because TCP has checksums and Ethernet has CRCs
- If it's inside my perimeter firewall, that means I have total control over it (@armorguy)
- If it doesn't return an error, then `send()` sent all the data that was asked of it.
- Packets arrive in the order in which they were sent.
- Segment boundaries on a TCP stream are meaningful to the application.
- Segment boundaries on a TCP stream are not meaningful to the application.
- If you can't ping the target, then it doesn't exist. (@jjarmoc)
- If you can ping the target, then it does exist.
- TCP RSTs come from end-nodes.
- Bytes must be "swapped" from the network byte-order to the host CPU byte-order.
- It's an internal web app -- outsiders won't be able to discover where it is (@biosshadow)
- The DHCP address will be the same after a reboot (@shewfig)
- The DHCP address will remain the same until the next reboot.
- Well, it'll last a long time between changes
- Packets/PDUs go up or down the network stack, never sideways. (@maradydd)
- The IPv4 header is 20 bytes long starting with 0x45 (options are so rare we don't have to worry about them) (@shewfig)
- The DHCP server and local router are the same (@schrotthaufen)

What's fun is that you can see these errors happen by monitoring  packets,   I started this list for programmers, but we inevitably drifted outside  programmers to network administrators. It's hard to draw the line,  because some misconceptions are shared by both.

- There is no IPv6 on my network (@shewfig)
- NAT automatically blocks all inbound attacks (@shewfig)
- We know all the devices attached to our network at any given time (@armorguy)
- VLANs are just as good as physical segmentation. (@jjarmoc)
- Ok, VLANs aren't as good, but they are good enough for now.
- We have good WIPS/monitors, so we don't have rogue access-points anywhere. (@armorguy)
- No need to add it to the DNS; I'll remember it. (@shewfig)

## Fallacies of distributed computing

- The [network](https://en.wikipedia.org/wiki/Computer_network) is reliable

  > Software applications are written with little error-handling on  networking errors. During a network outage, such applications may stall  or infinitely wait for an answer packet, permanently consuming memory or other resources. When the failed network becomes available, those  applications may also fail to retry any stalled operations or require a  (manual) restart.

- [Latency](https://en.wikipedia.org/wiki/Latency_(engineering)) is zero

  > Ignorance of network latency, and of the [packet loss](https://en.wikipedia.org/wiki/Packet_loss) it can cause, induces application- and transport-layer developers to  allow unbounded traffic, greatly increasing dropped packets and wasting  bandwidth.

- [Bandwidth](https://en.wikipedia.org/wiki/Throughput) is infinite

  > Ignorance of bandwidth limits on the part of traffic senders can result in bottlenecks.

- The network is [secure](https://en.wikipedia.org/wiki/Computer_security)

  > Complacency regarding network security results in being blindsided by  malicious users and programs that continually adapt to security measures.

- [Topology](https://en.wikipedia.org/wiki/Network_topology) doesn't change

  > Changes in [network topology](https://en.wikipedia.org/wiki/Network_topology) can have effects on both bandwidth and latency issues, and therefore can have similar problems.

- There is one [administrator](https://en.wikipedia.org/wiki/Network_administrator)

  > Multiple administrators, as with [subnets](https://en.wikipedia.org/wiki/Subnetwork) for rival companies, may institute conflicting policies of which  senders of network traffic must be aware in order to complete their  desired paths.

- Transport cost is zero

  > The "hidden" costs of building and maintaining a network or subnet are  non-negligible and must consequently be noted in budgets to avoid vast  shortfalls.

- The network is homogeneous

  > If a system assumes a homogeneous network, then it can lead to the same problems that result from the first three fallacies.
  
## Referenciass