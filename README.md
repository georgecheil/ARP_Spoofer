# ARP_Spoofer
This Python script is an implementation of an ARP (Address Resolution Protocol) spoofing tool using the Scapy library. 

ARP spoofing is a technique where an attacker sends falsified ARP (Address Resolution Protocol) messages over a local area network. 

It associates the attacker's MAC address with the IP address of a legitimate network resource (e.g., a router or another device), redirecting traffic to the attacker.

Here's a breakdown of the script:

1. **Imported Modules:**
   - `scapy`: A powerful packet manipulation library for network tasks.
   - `sys`: Provides access to some variables used or maintained by the Python interpreter.
   - `time`: Provides various time-related functions.

2. **Function Definition: `get_mac_address`**
   - Parameter: `ip_address` - the IP address for which the MAC address is to be resolved.
   - Functionality:
     - Creates an Ethernet frame with a broadcast destination MAC address.
     - Creates an ARP request packet with the specified target IP address.
     - Combines the Ethernet frame and ARP packet.
     - Sends the packet using Scapy's `srp` function and captures the response.
     - Returns the MAC address extracted from the response.

3. **Function Definition: `spoof`**
   - Parameters:
     - `router_ip`, `target_ip`: IP addresses of the router and the target machine.
     - `router_mac`, `target_mac`: MAC addresses corresponding to the router and the target.
   - Functionality:
     - Creates two ARP response packets (op=2) to spoof the ARP tables of the target and the router.
     - Sends the crafted ARP packets using Scapy's `send` function.

4. **Command Line Arguments:**
   - The script expects two command-line arguments: the IP address of the router (`sys.argv[1]`) and the IP address of the target machine (`sys.argv[2]`).

5. **Getting MAC Addresses:**
   - Retrieves the MAC addresses corresponding to the router and target IP addresses using the `get_mac_address` function.

6. **ARP Spoofing Loop:**
   - Runs an infinite loop to continuously send ARP spoofing packets.
   - Calls the `spoof` function with the relevant IP addresses and MAC addresses.
   - Pauses for 2 seconds between each iteration.

7. **Keyboard Interrupt Handling:**
   - Catches a `KeyboardInterrupt` exception (usually triggered by pressing Ctrl+C).
   - Prints a message indicating that the ARP spoofer is closing.
   - Exits the script.

8. **Note:**
   - ARP spoofing is a malicious activity and should only be performed in controlled environments for educational or authorized testing purposes. Unauthorized use of ARP spoofing is a violation of network security and privacy. Always ensure you have the necessary permissions before running such scripts.
  
Finally in order to forward packets we need to type the following command in the terminal
```
echo 1 >> /proc/sys/net/ipv4/ip_forward
```
