# Lab 2: Message Analysis using Wireshark

In this lab, you will learn to capture messages (Application, TCP segments, IP Packets and Ethernet Frames) using Wireshark. Wireshark is the world’s foremost and widely-used network protocol analyzer. It lets you see what’s happening on your network at a microscopic level and is the de facto (and often de jure) standard across many commercial and non-profit enterprises, government agencies, and educational institutions. Using packet analysis to sniff network traffic can achieve the following goals: Footprinting and reconnaissance. As a precursor to an active attack, hackers use Wireshark to capture unencrypted traffic in order to gather as much information about the target as possible.
We will not be hacking anything today, but we will learn how to build, define and exercise Wireshark Message/Packet Display Filter (Typing Text, Expression Builder & Shortcut options). You will also compare the standards of the TCP/IP Layered Network Architecture with Wireshark captured HTTP and TCP messages. More about TCP/IP Layered Network Architecture you can read [here](https://docs.oracle.com/cd/E19683-01/806-4075/ipov-10/index.html)

## 1. Setting up Wireshark
As you will be using Wireshark for this lab, let's learn how to setup Wireshark on Kali Linux inside Vagrant. 

**You can use your laptop (Linux system) (it is expected that you use Ubuntu for Desktops: http://www.ubuntu.com/ .) And VMware which is an open source on Linux systems.**

In the previous lab we were setting up Vagrant and VirtualBox VM, to make sure today lab is successful go to the vagrant file in your CS_Vagrant and delete it. 


**For this lab make new file otherwise it will not work!!!**

1. On your host machine, open a terminal in you home directory (or whatever directory you are asigned which has good memory). Make a directory `mkdir CS_Lab`
2. `cd CS_Lab` 
3. `vagrant init kalilinux/rolling`  
4. `vagrant up`. First time, this is will download Kali Linux. It will take a while. Once done, you will have new window opened! It is Kali Linux! 
5. Open a terminal inside Kali and type sudo wireshark. This will install Wireshark inside your Kali Linux VM! You screen should look something like [this](https://github.com/cs-uob/COMS20012/blob/master/docs/materials/Selection_001.png).
6. Congratulations! Now you are ready to run your first packet analysing lab!

**NOTE:** working from home?  If you need help post a question in the
Teams group for the unit and we'll try and help you from there, but if
at all possible do try and attend the lab where there will be *more* support. 

# Exercise 1: Wireshark Setup/Capture

Make sure that the Host Hardware/External Network Interface ethx (where x is an integer) is connected to the public network (Internet), that is, it acquired an IP address.

Launch Wireshark on the Host by typing sudo wireshark in a terminal on the Host. Click on the Interfaces option in the Capture menu. Click on the Options button corresponding to the IP address acquired by the Host Hardware/External Network Interface ethx.
Check the boxes for all Displays Options and Name Resolution. Make sure that “Enable promiscuous mode on all interfaces” is checked in. Click Start.

## Q1 - What does promiscuous mode mean?
+ **Promiscuous mode**: a mode that allows the network interface to pass all traffic it receives to the CPU rather than just the frames addressed to it.
+ Purpose: to enable the user to see all packets on the network, not just those directed to their network adaptor
+ Setting: ```Edit > Preferences > Capture ```
 <img width="551" alt="Screenshot 2024-05-28 at 12 51 05 AM" src="https://github.com/hyoyeon27/COMS20012/assets/117199082/4073e150-a558-4ce4-aa7f-3799a1a46a6b">

Wireshark should start displaying “packets” (actually displaying frames) transmitted or received on the selected interface. Note that each line represents an Ethernet Frame. Wireshark window is divided into 3 panes. If you do not see all 3 panes you may have to click on one of the thick horizontal divider to show any hidden pane. The top pane displays one row of info for each frame/packet captured.

## Q2 - Describe the information provided and explain the headings of the columns.
<img width="591" alt="Screenshot 2024-05-28 at 1 05 47 AM" src="https://github.com/hyoyeon27/COMS20012/assets/117199082/067007c3-b344-4c73-b75a-431bb590a81d">
Note that the frames/packets (rows) are sorted by Time. However, you can change that by clicking on the heading of another column and therefore sort by the heading of that column.

## Q3 – Provide an example where you have sorted the frames using the Protocol column.
The center pane displays the protocols associated with the selected Frame and the bottom pane displays the hexadecimal representation (Hex View) of the data contained in the same. Beneath the bottom pane is a status bar that displays the total number of Frames captured, displayed and marked (zero unless filtering is applied).

For example, if you select in the center pane the Ethernet II layer (Data Link) of a Frame, the hexadecimal representation of that layer information should be highlighted in the bottom pane. Take a [screenshot](https://github.com/cs-uob/COMS20012/blob/master/docs/materials/ScreenshotDNS.png).

## Q4 – Find out and describe how one could change the bottom pane view from Hex View to Bits.
+ ```Drag the hex val > ... as decimal```
+ The hex value represents the raw vinary data of the packet.


## Q5 – Explain the how one would go about converting decimal number 87 into its Hex and Binary representations.
<img width="468" alt="Screenshot 2024-05-28 at 1 10 44 AM" src="https://github.com/hyoyeon27/COMS20012/assets/117199082/034a19f0-0531-4a56-a9cc-3236bd3e3764"> <br>
+ Hex: ```Show bytes as hexadecimal```
+ Binary: ```...as binary```



# Exercise 2: Capturing Frames and encoding:
## Network Packet Capture and Analysis
**1. Open FireFox Browser on host**
    + Navigate to `Edit > Preferences > Privacy`.
    + Select "Never remember history".
    + Click on "Clear all current history" and then click "Close".
    + Ensure the startup home page is set to Google or Ubuntu Google.
    + Close the browser.

**2. Restarting Capture in Wireshark**
   + Open the Wireshark application.
   + Select `Capture > Restart(green arrow)`from the top menu bar
   + All previously captured and displayed frames will be cleared from the top pane.
   + **Note**: New frames will be captured almost instantaneously due to continuous network activity.

**3. Generating DNS Requdsts**
   + Open a terminal on the Host machine.
   + Type the command nslookup google.com to generate Domain Name System (DNS) requests.
   + This command forces the generation of DNS requests, which can then be captured and analyzed in Wireshark.

**4. Analysing Captured Packets**
   + Return to Wireshark and observe the captured packets in the top pane.
   + Look for DNS requests and response packets generated by `nslookup` command.
     
<img width="614" alt="Screenshot 2024-05-28 at 1 17 50 AM" src="https://github.com/hyoyeon27/COMS20012/assets/117199082/8b6ce50d-facc-49ce-8dec-c142102bf71e">

  + DNS server: being queried (10.0.2.3)
  + Address of DNS server: 10.0.2.3#53

## Q6 – compare the results of nslookup on the Host terminal and the content of the corresponding DNS response message as captured by Wireshark.
: The IP addresses and details obtained from `nslookup` with the DNS response should match.
+ This shows that the DNS query made by `nslookup`corresponds to the DNS response packet captured by Wireshark.

## HTTP Traffic and Protocol Analysis
**1. Generate HTTP Traffic**
   + Open Firefox browser on the host and navigate to a website to generate HTTP requests and responses, along with TCP segments.
   + Wireshark should capture various protocols such as ARP, DNS, TCP, HTTP, etc.

**2. Capture and Save Traffic**
  + Start capturing packets with Wireshark before launching the browser.
  + Stop tshe capture after a second or two and save the captured packets using `File > Save` As in Wireshark.



## Exercise 3: Wireshark Display/Filtering
**Filter tool bar**: a bar where you can type filter expressions to display only specific types of traffic. 
<img width="644" alt="Screenshot 2024-05-28 at 1 25 20 AM" src="https://github.com/hyoyeon27/COMS20012/assets/117199082/e0391a41-c3d7-4691-93ce-7640182f44e4"> <br>

  + Type `http` in the tool bar text box and click `Apply`.
  + The background of the text box turns green when syntax is correct.
  + Wireshark display Frames with `http protocol` (as the top protocol).
  + Type `tcp` in the tool bar text box and click `Apply` (will display TCP packets only).

## Q8 - Why are there some frames labeled as HTTP under the protocol heading after applying the tcp filter?
If you need to exclude the HTTP from the TCP frames, you can type “tcp and not http” (which means filter for tcp and exclude http) in the filter text box. Try it out. Provide your results. For more information regarding wireshark filters check the following link.

<img width="378" alt="Screenshot 2024-05-28 at 1 29 22 AM" src="https://github.com/hyoyeon27/COMS20012/assets/117199082/e6e2082e-5d2a-4b76-b6e3-0ac1521905c7"> <br>

+ `ìp.src == <ip.address>`
  : display packets sent from a specific IP address <br>
<img width="299" alt="Screenshot 2024-05-28 at 1 39 49 AM" src="https://github.com/hyoyeon27/COMS20012/assets/117199082/071e8e66-4e47-4284-a4f6-ddd547ea4d70"> <br>

To find out the entire set of Display Filter syntax, you may click the Expression button next to the filter text box. For example, scroll to the IP entry and expand by clicking on the + sign or the arrow on the left. Wireshark should display all possible attributes of the object IP. Find ip.ttl and find out what it means. Type “ip.ttl” then “==” and type “64” in the value field so that the equation would look like the following (ip.ttl == 64) and Click OK.
## Q9 - Describe what happens (what you have witnessed).
## Q10 – Can I filter for a specific source IP address and specific destination IP address? Provide screenshots.
<img width="332" alt="Screenshot 2024-05-28 at 1 41 48 AM" src="https://github.com/hyoyeon27/COMS20012/assets/117199082/0bef71de-a52c-4bbb-a965-46b13e399500"> <br>

+ ìp.src == <ip.address> and ip.dst == <ip.address>`


