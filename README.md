<h1>Azure Sentinel Lab</h1>
<br/>
<h2>Description</h2>
In this lab, I deploy a VM in Azure, ingest logs into Log Analytics Workspace, and then configure Azure Sentinel to display global attack data (RDP brute force) on a world map according to physical location and magnitude of attacks. 
<br />


<h2>Languages and Azure Services Used</h2>

- <b>PowerShell</b> 
- <b>Azure Sentinel</b>
- <b>Log Analytics Workspace </b>
- <b>Virtual Machines</b>

<h2>Environments Used </h2>

- <b>Windows 10</b> (22H2)

<h2>Lab walk-through:</h2>

<p align="center">
Log into your Azure account and create a virtual machine. <br/>
<img src="https://imgur.com/koe4u0e.png" height="80%" width="80%"/>
<br />
<br />
Create a Resource group for your VM, give your VM a name, and select an image. For this lab, we'll be using a Windows 10 (22H2) Image. Scroll down to enter a username and password for your VM and then head to the networking tab.  <br/>
<img src="https://i.imgur.com/GqbVfQM.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
For the NIC network security group, select 'advanced' and then 'create new' <br/>
<img src="https://i.imgur.com/9EW9DDe.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Remove the default rule.  <br/>
<img src="https://i.imgur.com/bvT267Z.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Create a new inbound security rule. The '*' allows for all port ranges. We want to make our VM enticing to potential attackers.  <br/>
<img src="https://i.imgur.com/90utViX.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Create a Log Analytics Workspace, add it to the same resource group as your VM, and name it.   <br/>
<img src="https://i.imgur.com/AQGDr8V.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<img src="https://i.imgur.com/JOF3qNM.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Navigate to Microsoft Defender> Environment settings > your log analytics workspace.  <br/>
<img src="https://i.imgur.com/TOMFchR.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Set 'SQL servers on machines' to 'off'  <br/>
<img src="https://i.imgur.com/V1YII98.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Click on the 'Data collection' tab and select 'All events'. <br/>
<img src="https://i.imgur.com/iv6BrGO.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Connect your log analytics workspace to your VM so that you can ingest logs. <br/>
<img src="https://i.imgur.com/d1HhyYk.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<img src="https://i.imgur.com/AypefVQ.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Add Azure Sentinel to your log analytics workspace. <br/>
<img src="https://i.imgur.com/KCuZolw.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<img src="https://i.imgur.com/IrhezJE.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Use Remote Desktop Connection to connect from your computer to the VM. (Login incorrectly at first) <br/>
<img src="https://i.imgur.com/8hRwNHQ.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Once your connected to your VM, open up event viewer and try to find where your unsuccessful RDP login was logged. It Should be under Event ID 4625. The log shows the username that the attacker used and their IP address. These are the logs that we want to ingest into our log analytics workspace, but before we do that, we will send these logs out to an API that will provide us with the longitude and latitude of our attackers. <br/>
<img src="https://i.imgur.com/E76dhUu.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
<img src="https://i.imgur.com/YxJx3oJ.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Turn off Windows firewall on the VM, and then Download and run the powershell script labled 'Custom_Security_Log_Exporter.ps1' (located within this repository). You will have to navigate to ipgeolocation.io and sign up to get your own API key. This API will return the longitude and latitude of an attacker based off their IP address.
<img src="https://i.imgur.com/CizaMvX.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Navigate to where the custom logs are being outputted on your VM. 'C:\ProgramData\failed_rdp.log'  <br/>
<img src="https://i.imgur.com/7sGCMZv.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Copy the contents of the log, save it as a text file and store it on the desktop of your real computer. We are going to uses this as a sample for the creation of our custom log in Log analytics worksapace.  <br/>
<img src="https://i.imgur.com/ykHphlU.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Navigate to your Log Analytics Workspace > Tables > Create new custom log (MMA based). <br/>
<img src="https://i.imgur.com/3Hdd2WV.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Upload the sample file that you stored on your desktop. <br/>
<img src="https://i.imgur.com/sxh5mk5.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Enter the file path for where the custom logs are being outputted in the VM. 'C:\ProgramData\failed_rdp.log' <br/>
<img src="https://i.imgur.com/xSxa1HV.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Add a workbook to Azure Sentinel. <br/>
<img src="https://i.imgur.com/N8fJfKS.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Select 'Add query' and paste in the Log Analytics Workspace Query provided as a file within this repository <br/>
<img src="https://i.imgur.com/uVKArJH.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br/>
<br/>
This is the product. The map shows 2 failed RDP logins from the Pennslyvania area (when I purposely failed to login)
<img src="https://i.imgur.com/JdkUkM3.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
After a few more hours, there is a lot more action. 89 failed RDP logins from India!
<img src="https://i.imgur.com/a7cU54L.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
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
