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
Microsoft Defender  <br/>
<img src="https://i.imgur.com/TOMFchR.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
<img src="https://i.imgur.com/V1YII98.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
<img src="https://i.imgur.com/iv6BrGO.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
<img src="https://i.imgur.com/d1HhyYk.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
<img src="https://i.imgur.com/AypefVQ.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
<img src="https://i.imgur.com/KCuZolw.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
<img src="https://i.imgur.com/IrhezJE.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
<img src="https://i.imgur.com/8hRwNHQ.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
<img src="https://i.imgur.com/E76dhUu.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
<img src="https://i.imgur.com/YxJx3oJ.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
use script  <br/>
 <br/>
 <br/>
 <br/>
<img src="https://i.imgur.com/7sGCMZv.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
<img src="https://i.imgur.com/ykHphlU.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
<img src="https://i.imgur.com/3Hdd2WV.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
<img src="https://i.imgur.com/sxh5mk5.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
<img src="https://i.imgur.com/xSxa1HV.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
<img src="https://i.imgur.com/N8fJfKS.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
<img src="https://i.imgur.com/uVKArJH.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
use query   <br/>
<br/>
<br/>
<br/>
<img src="https://i.imgur.com/JdkUkM3.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
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
