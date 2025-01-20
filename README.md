<h1>Snort 3.0 Setup Tips</h1>

<p>Follow this official guide from Snort's website</p>
<b></b>
[Snort 3.1.18.0 on Ubuntu 18 & 20](https://www.snort.org/documents/snort-3-1-18-0-on-ubuntu-18-20)

<h2>Description</h2>

Project consists of a few setup tips for Snort 3 to and writing some detection rules since there isn't much guidance out there apart from some very basic examples.
<br />

I included the .lua file as well as the .rules file as it's a functional configuration
<br/>

<p>Note that there's a mistake in the documentation when setting up OpenAPPID. It's where you save the ODT file and hence, changing the path you specify for in the snort.lua file</p>

<h2>Setup is on Ubuntu</h2>

<p>I set it up on Ubuntu, since not all distros have the same package list. You will run into many errors midway trying to set Snort 3 up on Kali if you are doing a manual build</p>


<h2>Program walk-through:</h2>

<p align="center">
Launch the utility: <br/>
<img src="https://i.imgur.com/62TgaWL.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Select the disk:  <br/>
<img src="https://i.imgur.com/tcTyMUE.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Enter the number of passes: <br/>
<img src="https://i.imgur.com/nCIbXbg.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Confirm your selection:  <br/>
<img src="https://i.imgur.com/cdFHBiU.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Wait for process to complete (may take some time):  <br/>
<img src="https://i.imgur.com/JL945Ga.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Sanitization complete:  <br/>
<img src="https://i.imgur.com/K71yaM2.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Observe the wiped disk:  <br/>
<img src="https://i.imgur.com/AeZkvFQ.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
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
