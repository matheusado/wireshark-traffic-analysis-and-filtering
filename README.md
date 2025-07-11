<h1>Wireshark-traffic-analysis-and-filtering</h1>


<h2>Description</h2>
This project demonstrates network traffic analysis and packet filtering using Wireshark. It involves capturing Ethernet packets, applying display filters to isolate HTTPS traffic, and identifying the IP addresses of visited websites. The goal is to gain hands-on experience in analyzing network traffic dynamics and improve skills in packet-level inspection using industry-standard tools.
<br />


<h2>Languages and Utilities Used</h2>

- Wireshark – for capturing and analyzing network traffic
- Display Filters (Wireshark Syntax) – for filtering HTTPS and IP-specific packets
- TCP/IP Protocol Suite – underlying protocol stack for packet analysis
- Ethernet – network layer used for capturing traffic
- Browser (e.g., Chrome, Firefox) – to generate HTTPS traffic during capture

<h2>Environments Used </h2>

- <b>macOS Ventura 13.7.4</b> (21H2)
- Virtualization Platform: VirtualBox
- Guest Operating System: Kali Linux
- Wireshark Interface: Ethernet or Wi-Fi network interface for live traffic capture

<h2>Program walk-through:</h2>

<p align="center">
Double-click on Wireshark to open it and select eth0: <br/>
<img src="https://i.imgur.com/D7AxmrG.png"/>
<br />
<br />
Once the eth0 interface has been selected, click the Start capturing packets button on the top left:  <br/>
<img src="https://i.imgur.com/eUAOLsp.png"/>
<br />
<br />
The application will display an empty capture screen initially: <br/>
<img src="https://i.imgur.com/OltjMab.png"/>
<br />
<br />
Now, open a browser window and search for any website (for example, https://duckduckgo.com):  <br/>
<img src="https://i.imgur.com/Tc2xp74.png"/>
<br />
<br />
Switch to the Wireshark tool to see the packets being captured:  <br/>
<img src="https://i.imgur.com/5Elc9Zc.png"/>
<br />
<br />
Now to save this output to a file, click on the Stop capturing packets button (Red Square) on the top left to stop the capture:  <br/>
<img src="https://i.imgur.com/kAEIudn.png"/>
<br />
<br />
Then click the File option on the top left:  <br/>
<img src="https://i.imgur.com/Ik0yuER.png"/>
<br />
<br />
Click Save As from the dropdown. Give a name to the capture file and click Save:  <br/>
<img src="https://i.imgur.com/7VPejLq.png"/>
<br />
<br />
Use a display filter to detect HTTPS packets. Click on the Apply a display filter field:  <br/>
<img src="https://i.imgur.com/mNG2nQg.png"/> 
<br />
<br />
Type tcp.port == 443 in the display filter field and click Enter to apply the filter on TCP port 443. Only HTTPS packets will be filtered and visible on the packet screen:  <br/>
<img src="https://i.imgur.com/VwRqQHu.png"/>
<br />
<br />
Under the Info column, search for the packet named ‘Client Hello’:  <br/>
<img src="https://i.imgur.com/CBS2YJP.png"/>
<br />
<br />
Copy and paste the destination IP address on the browser:  <br/>
<img src="https://i.imgur.com/CW7GlGn.png"/>
<br />
<br />
The page will redirect to duckduckgo.com. This IP address will forward the request to the client website you visited earlier:  <br/>
<img src="https://i.imgur.com/t3bEnwY.png"/>
<br />
<br />
Clear the current captured packets and start a new capture. Then visit another web page and detect its IP address using a display filter:  <br/>
<img src="https://i.imgur.com/AU0KmKm.png"/>
<br />
<br />
Navigate to the browser to enter https://www.google.com:  <br/>
<img src="https://i.imgur.com/ePDYi0s.png"/>
<br />
<br />
Now, stop the capture process:  <br/>
<img src="https://i.imgur.com/BXyRyhj.png"/>
<br />
<br />
Enter tls.handshake.type ==1 in the display filter field to identify a website visit within the packet list:  <br/>
<img src="https://i.imgur.com/3c1q91s.png"/>
<br />
<br />
Enter tls.handshake.type ==1 in the display filter field to identify a website visit within the packet list:  <br/>
<img src="https://i.imgur.com/6degXpG.png"/>
  
Note: The following activity will filter for 142.250.176.4 as the specific IP address. IP addresses listed in your packet list may vary.
<img src="https://i.imgur.com/7jljowN.png"/>
<br />
<br />
Enter ip.addr==142.250.176.4 in the display filter field to retrieve packet information for a particular website.

Note: The application will display all the packets related to the desired IP address. The desired IP address can be listed under the Source or the Destination columns:  <br/>
<img src="https://i.imgur.com/ZK9PW3c.png"/>
<br />
<br />
Use ip.src == 142.250.176.4 to filter the Source column for the specific IP address:  <br/>
<img src="https://i.imgur.com/HtkO7O8.png"/>
<br />
<br />
Use ip.dst == 142.250.176.4 to filter the Destination column for the specific IP address:  <br/>
<img src="https://i.imgur.com/Gg7cR4R.png"/>
<br />
<br />
Use ip.dst == 142.250.176.4 to filter the Destination column for the specific IP address:  <br/>
<img src="https://i.imgur.com/Gg7cR4R.png"/>
<br />
<br />
Locate all HTTPS packets from a capture not containing a certain IP address, in this case the one we've been using (142.250.176.4). Use conditional statements in Wireshark to include or exclude packets from the capture: !(ip.addr == 142.250.176.4):  <br/>
<img src="https://i.imgur.com/wmAC0uB.png"/>
<br />
<br />
Add multiple filters for doing precise scanning and understanding of the traffic. 

!(ip.addr == 142.250.176.4) and tcp.port == 443

NOTE: It’s important to use parentheses in compound conditionals to prevent errors in the execution order:  <br/>
<img src="https://i.imgur.com/zwWhHPe.png"/>

This project provided practical experience in capturing and analyzing network traffic using Wireshark on a Kali Linux virtual machine. By applying display filters and identifying HTTPS packet data, I gained deeper insight into network protocols, packet structures, and traffic behavior. This exercise enhanced my skills in real-time traffic inspection and laid a strong foundation for future work in network security and threat analysis.
<br />
<br />
</p>

<!--
 ```diff
- text in red
+ text in green
! text in orange
# text in gray
@@ text in purple (and bold)@@
```
--!>
