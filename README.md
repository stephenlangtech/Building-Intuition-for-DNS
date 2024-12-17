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
<img src="" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<img src="" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<p>
Now we will change the record address of "mainframe" to 8.8.8.8 if we go back to the client machine it will still ping the old adress even though we changed it. That is because we have to flush the DNS with the command ipconfig /flushdns. That will clear the DNS cache, when we attempt to ping mainframe again the address of the new record will show. 
</p>
<br />

<p>
<img src="" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Now we will change the record address of "mainframe" to 8.8.8.8 if we go back to the client machine it will still ping the old adress even though we changed it. That is because we have to flush the DNS with the command ipconfig /flushdns. That will clear the DNS cache, when we attempt to ping mainframe again the address of the new record will show. 
</p>
<br />

<p>
<img src="" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Now we will change the record address of "mainframe" to 8.8.8.8 if we go back to the client machine it will still ping the old adress even though we changed it. That is because we have to flush the DNS with the command ipconfig /flushdns. That will clear the DNS cache, when we attempt to ping mainframe again the address of the new record will show. 
</p>
<br />
