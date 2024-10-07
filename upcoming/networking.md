# Networking

- What are subnets
- What is the role of the NAT, WAF, Internet Gateway and API Gateway.
- What is a routing table.
- Chat about the DNS at a decently high level.
- What is a VPC 
- What is a VPN 
   - What is the purpose of a VPN
- Chat about TCP vs UDP
- Then quick piece on what SSL and TLS is

Up until very recently I was somewhat intimidated by the network details of my role as a software engineer. I feel as if this changed for two reasons; implicitly working with these elements on a daily basis and taking some time to research them in a little more detail with the benefit of this experience.
So what did I learn or maybe more accurately what did I understand in more detail than I did when I was initially introduced to al of this back in my degree. In line with some advice I received from a senior colleague that it may be best to start from bottom up with technical learnings I think that that could be the best approach here also.
So what does bottom up mean in this context?

Well that my friend is pretty straightforward thankfully.
Start down at the bits level which is the data layer I believe. Fibre optic cables, copper? Cables and radio waves in the case of wifi ( there is a good article out there on what 5g means in this context)
I can outline all the different OSI layers when I write this all up more correctly when I do some more detailed research.
Then next up thanks to some computerphile videos the IP layer is pretty straightforward. IP regions are controlled by IANA or one of those acronymns that it doesn’t even make any difference to know who they are. But countries will be assigned certain ranges. This is changing from IPv4 to IPv6 at the moment so can outline the changes there. I think it’s just a good few more bytes than IPv4 catered for which was potentially just 4 bytes?
Within this then there is the notion of private IP vs public IP. Within your home network you will be assigned a private IP I believe but all traffic will be aggregated back to your home network.
This probably ties in nicely with DHCP for like asssignment of an IP within a subnet? Is this the right place to reference subnet not really sure. Can chat about what CIDR means as well here. Then the other thing is how this works with a VPN and how that is all enforced and what the benefits/risks are of this.

Cool this is the outmost layer and DNS is like a step above this then really I suppose converting your domain requested to an IP address. But as I write this I wondering how DNS is resolved so that the link layer can llke map it all the way out.

I believe the higher level protocols depend on the lower level ones. So I would think the link layer would requre dns to be resolved so that it could do its thing to be fair.
Then ARP does need to take place to resolve the IP address to a MAC address. Once again this seems to be going from top down as opposed to bottom up so not sure what’s going on here. Need to figure out the order of dependencies here and how that operates in practice.

Ok so say we now know the path to the server what next?
Well then we’ll need to set up a protocol to manage the transfer of data.
TCP over IP what is the significance of over IP? Would seem to be the main one which has some more guarantees about the ordering of data
But at this point if you were to continue to send you http message then it would be out in the open.
So actually does this mean that http packets can’t be sent all in one message or what is the crack?
Can the http part not only be sent after the the TCP and then TLS connection are set up?
Just have a lot of questions on dependencies here really.

Finally that’s all encrypted so can send the http request across.

Cool so will need to clarify this but it seems like http request invokes dns resolution so that that information can be passed down to the IP layer to actually get in contact with the computer.
Then only after TLS connection is secured in the case of https will the content of the request be sent.

e.g so request to the stripe api would have to resolve the host IP for that post request
But the actual contents would only be sent with card details after the connection is secured
