<p align="center">
<img src="https://i.imgur.com/CtGfsq8.png" alt="osTicket logo"/>
</p>

<h1>Building Intuition for DNS</h1>
In this lab, we will explore and experiment with the Domain Name System (DNS) to gain a deeper understanding of how it operates and supports network communication. Through practical exercises, we aim to enhance our knowledge of DNS functionality and its critical role in translating domain names into IP addresses.<br />

<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines/Compute)
- Remote Desktop
- DNS

<h2>Operating Systems Used </h2>

- Windows 10</b> (21H2)

<h2>List of Prerequisites</h2>

- A Virtual Machine with Active Directory
- A Client VM joined to your Network 

<h2>Lab Steps</h2>
<p>
<img src="https://i.imgur.com/2Wl0nRt.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
First, start the VMs and RDP into Client1. Open PowerShell as an administrator and attempt to ping "mainframe." This will fail because "mainframe" is not found in the local cache, the hosts file, or the DNS server.
</p>
<br />

<p>
<img src="https://i.imgur.com/4IPXilR.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Next, run the command ipconfig /displaydns. You'll notice there is no entry for "mainframe" in the DNS cache.
</p>
<br />

<p>
<img src="https://i.imgur.com/XbNuQE3.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
After that, run the command nslookup mainframe. Once again, you'll find that no results are returned.
</p>
<br />

<p>
<img src="https://i.imgur.com/pwQioSl.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Next, we'll create a DNS A-record on DC-1 for "mainframe" and point it to DC-1's private IP address. On the DC-1 VM, search for Administrative Tools and open DNS. Navigate to DC-1 > Forward Lookup Zones > mydomain.com, then right-click inside mydomain.com and select New Host (A or AAAA). In the Name field, enter mainframe, and in the IP Address field, input DC-1's private IP address. Save the record.
</p>
<br />

<p>
<img src="https://i.imgur.com/zMrBLqR.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Now, return to Client1 and try pinging "mainframe" in PowerShell again. This time, the ping will succeed because we created a DNS A-record on DC-1 pointing to its private IP address.
</p>
<br />

<p>
<img src="https://i.imgur.com/hRa9Zos.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<img src="https://i.imgur.com/xWA0TfZ.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Now, go back to DC-1 and update the DNS A-record for "mainframe" to point to the IP address 8.8.8.8. After making this change, return to the Client1 VM and ping "mainframe" again. You'll notice it still pings the old IP address.
</p>
<br />

<p>
<img src="https://i.imgur.com/8nSHNtq.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Use the command ipconfig /displaydns on Client1 and locate the entry for "mainframe." You'll see that the A-record still points to 10.0.0.4, providing a more detailed view of the cached DNS entry.
</p>
<br />

<p>
<img src="https://i.imgur.com/K7BQDEu.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
To ensure that the new IP address from the updated A-record is reflected, use the command ipconfig /flushdns to clear the DNS cache. After this, the new IP address will be shown when you use ipconfig /displaydns.
</p>
<br />

<p>
<img src="https://i.imgur.com/BGKH5xK.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Now, attempt to ping "mainframe" one more time from Client1. You'll notice that it successfully pings the new IP address 8.8.8.8, reflecting the updated A-record.
</p>
<br />

<p>
<img src="https://i.imgur.com/1Idq19o.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Next, go back to the DC-1 VM and create a CNAME record that points the host "explore" to "www.google.com". To do this, navigate to the DNS Manager, right-click mydomain.com under Forward Lookup Zones, and select New Alias (CNAME). In the Alias name field, enter explore, and in the Fully Qualified Domain Name (FQDN) field, enter www.google.com. Save the record.
</p>
<br />

<p>
<img src="https://i.imgur.com/SI2VH6B.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Go back to the Client1 VM and ping "explore." You should observe that the ping is successfully resolved to www.google.com, as the CNAME record you created points "explore" to that address.
</p>
<br />

<p>
<img src="https://i.imgur.com/ys286eQ.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Lastly, run the command nslookup explore on Client1. The results should show that "explore" resolves to www.google.com, indicating the CNAME record is working as expected.
</p>
<br />
