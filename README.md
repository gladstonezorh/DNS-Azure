# DNS-Azure<p align="center">
<img src="https://i.imgur.com/pU5A58S.png" alt="Microsoft Active Directory Logo"/>
</p>

<h1>Understanding DNS in a Domain Controller</h1>
This tutorial extends the on-premises Active Directory and demonstrates creating A-Records and CNAME Records in Active Directoty. Also, this tutorial explores the need for Domain Name System (DNS).<br />

<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines/Compute)
- Remote Desktop
- Active Directory Domain Services
- Command Line

<h2>Operating Systems Used </h2>

- Windows Server 2022

<h2>Active Directory and DNS Exercise</h2>

- A-Records in Active Directory
- Local DNS Cache
- CNAME Record in Active Directory

<h2>Creating A-Records in Active Directory</h2>
<p>
<img src="https://imgur.com/Vq7LKbz.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
After logging into the Domain Controller and Client computer, we can login to the Server Manager under the Domain Controller, --> click on "Tools" and "DNS" Inside of DNS, we can create A-Name Records under Forward Lookup Zones. This zone allows you to map hostnames to IP address in Active Directory and reviews the current A-records that were created when Active Directory was installed. Reserve lookup zone allows you to to map IP addresses to hostnames. To create a new A-Record, right-click inside of "domain url under Forward Lookup Zones", select "New" and "New Host (A or AAA). For this exercise, create "mainframe" as parent domain and copy and paste the DC's Private IP address from the Microsoft Azure Portal. Next, ping "mainframe" in Command line in Client 1 to review that the ping has succeeded and replies to the hostname's DNS.
</p>
<br />
<h2>Exploring DNS Cache</h2>
<p>
<img src="https://imgur.com/kMJS8WN.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Inside of the DC, we can edit the A-record "mainframe" by updating the IP address to 8.8.8.8. Next, we can go back to Client 1 and ping "mainframe" in the command line and observe that the old IP address still remains. To observe the local DNS cache we can enter "ipconfig /all" to see that the old IP address is still listed. Next, we can flush the DNS cache by entering "ipconfig /flushDNS" to remove the previous cache. Lastly, we can ping "mainframe" again and observe that the new IP address was added, as the previous cache was flushed. This exercise showcases the importance of flushing cache and ensuring that they DNS is up-to-date.
</p>
<br />
<h2>Creating CNAME Records in Active Directory</h2>
<p>
<img src="https://imgur.com/Ke92Fd6.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Inside of the Server Manager, we can create CNAME Records, as well. This record will point the host name to a target host (i.e. website). Thus, we can right click under Forward Lookup --> click on "New" and "Alias CNAME". Next, we can ping "search" and "nslookup in command line on Client-1 to review that the hostname "search" points toward the "website" (ie. google.com).
</p>
<br />
