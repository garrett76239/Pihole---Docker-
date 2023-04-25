# Pihole---Docker

I have setup 2 versions of the Pihole DNS sinkhole. One version is running on a Raspberry Pi Zero W and the other is a modified version that can run on a laptop. The original program was never intended to run on anything other than Pi hardware so the laptop version does occasionally have issues. I wanted it so that when I took my laptop to class, the Pihole that the laptop was running would serve as the systems own DNS sinkhole. However, when connecting to the college wifi the IP address would change from day to day. Rather than run a command to manually change the laptops DNS address I wrote a bash script that would pull the systems current IP address and change the DNS address to that IP address so that it would serve as its own DNS sinkhole.

Bash script I wrote in order to quicky make my laptop IP address and DNS address the same:


#!/bin/bash

#pull system IP address and make it the DNS address
printf "nameserver $(hostname -I | awk '{ print $1 }')" > /etc/resolv.conf

#list docker containers
sudo docker ps

printf "\n
printf "\n"

#verify that IP address and DNS address match
printf "Current Device IP address: $(hostname -I | awk '{ print $1 }')"

printf "\n"

#verify that IP address and DNS address match
printf "Current DNS IP address: $(dnsdomainname -I | awk '{ print $1 }')"




Acknowledgements for the original project source code: https://github.com/theNetworkChuck/NetworkChuck/blob/master/pihole.sh
