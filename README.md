Ubuntu 14.04.1 LTS with vblade. Block level Storage Area Network (SAN) based on the ATA over Ethernet (AoE) protocol.

This build of the container is suitable for demos, testing, evaluation, proof-of-concepts and training. vblade is designed to provide a free AoE SAN target in software. Hardware AoE SAN equipment and appliances with greater performance, scalability and feature sets than vblade can be purchased from Coraid resellers like us.

To run the vblade container on the same physical Docker host with the AoE initiator container, use the following:

sudo docker run -i -t symlogix/vblade bash

To run the vblade container on one Docker host and the AoE initiator container on a different Docker host while sharing the same Ethernet switch:

sudo docker run -i -t --net=host symlogix/vblade bash

******* Please note that there are two dashes before net=host *******


|Quick start on a running vblade container|

1) Create a raw image file (for this example - 10GB)
      mkdir /test
      dd if=/dev/zero of=/test/raw_image.raw bs=1M count=10000
  
2) Run vblade process (for example with settings for shelf #2, slot #1)
      vblade 2 1 eth0 /test/raw_image.raw
      
3) vblade process will continue to operate until you press <CTRL> + <C>

4) Use the AoE initiator container to connect to the vblade exported raw image file. See: https://registry.hub.docker.com/u/symlogix/aoe_initiator/


|Limitations|

a) Like many SANs, there is usually a one-to-one relationship between a SAN target (e.g. vblade) and the initiator (in many places this could be a NAS or server). A vblade container should only be read/write accessed by a single AoE initiator. A clustered file system is required if you plan to have your vblade SAN target support multiple, simultaneous AoE initiators. On the other hand, a single AoE initiator can simultaneously access multiple vblade or AoE SAN targets. This makes distributed, network (gigabit per second speeds and higher) RAID very possible - powerful, flexible and fast.


|Problems|

a) vblade-persist is installed but appears to be malfunctioning within this build at this time. To be investigated.


Questions? Contact us: https://www.symlogix.com/contact/


Related links:

https://www.symlogix.com/products/storage/coraid/
https://en.wikipedia.org/wiki/ATA_over_Ethernet
http://support.coraid.com/documents/AoEr11.txt
