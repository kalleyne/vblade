Ubuntu 14.04.1 LTS with vblade. Block level Storage Area Network (SAN) based on the ATA over Ethernet (AoE) protocol.

When placing vblade on the same physical Docker host with the AoE initiator, use the following:

<code>sudo docker run -i -t symlogix/vblade /bin/bash</code>

When placing vblade on one Docker host and the AoE initiator is on a different Docker host sharing the same Ethernet switch:

<code>sudo docker run -i -t --net=host symlogix/vblade /bin/bash</code>

Additional details to follow.

Questions? Contact us: https://www.symlogix.com/contact/
