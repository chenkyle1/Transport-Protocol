# CS3700 Project 4: Reliable Transport Protocol

Steven Ngo and Kyle Chen

## High Level Approach
This project simulated a simple transport protocol that provides a reliable datagram service. We followed along with
the suggested implementation approach which completed the tests one level at a time. The first step was to simply
send and receive and ack packet. Consequently, we had to implement the ability to resend packets, which we did
by storing packets in a dictionary and comparing their sequence numbers and timestamps. The ability to resend
packets was utilized in out of order, duplicate or dropped packets, where these respective packets would be resent.
Each of these scenarios had their own method of being detected. Next, we detected corrupt packets by determining if
they were in the valid format and had the correct checksum value. Lastly, we modified our code to allow different
latencies and bandwidths to be supported.

## Challenges
Some challenges we faced was detecting how some packets are dropped and out order. We had to implement sequence numbers
as well as timestamps for each of messages and determine if the received numbers and timestamps matched the expected
ones. In order to resend the packets, we also had to keep track of not only the packets that were sent and received
but also what order to send them in, which proved to be a difficulty. Another challenge was how to calculate the
checksum because it appeared to have multiple binary steps, which we went through multiple iterations of approaches
before settling on our current one.
 
## Features
Our implementation supports sequence numbers and timestamps of packets, which enables the sender and receiver to detect
if packets are dropped, out of order or duplicated. Similar to the three-way handshake of TCP, we send and receive
and initial ack packet to ensure that our connection is secure prior to the transmission. As mentioned in the prior
section, we also support the calculation of checksum values

## Testing
To test our protocol, we ran each level of config tests after our implementation of a feature. We also utilized the
logging library print messages at various points in our code, which we used to ensure it worked correctly, as well
as to debug