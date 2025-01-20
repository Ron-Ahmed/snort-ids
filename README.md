<h1>Snort 3.0 Setup Tips</h1>

<p>Follow this official guide from Snort's website</p>
<b></b>
[Snort 3.1.18.0 on Ubuntu 18 & 20](https://www.snort.org/documents/snort-3-1-18-0-on-ubuntu-18-20)

<h2>Description</h2>

Project consists of a few setup tips for Snort 3 to and writing some detection rules since there isn't much guidance out there apart from some very basic examples.
<br />

I included the .lua and .rules file as it's a functional configuration that works with Pullpork plugin
<br/>

<p>Note that there's a mistake in the documentation when setting up OpenAPPID. It's where you save the ODT file and hence, changing the path you specify for in the snort.lua file</p>

<h2>Setup is on Ubuntu</h2>

<p>I set it up on Ubuntu, since not all distros have the same package list. You will run into many errors midway trying to set Snort 3 up on Kali if you are doing a manual build</p>


<h2>Program walk-through:</h2>

<p align="center">
Create a backup of the original .lua file, this way you revert back to it in case your break the configuration with a change: <br/>
<img src="https://i.imgur.com/aiODyob.png" height="80%" width="80%" alt="configuration file backup"/>
<br />
<br />
sudo snort -c /usr/local/etc/snort/snort.lua --plugin-path /usr/local/etc/so_rules/ -i ens33 -A alert_fast -s 65535 -k none -R /usr/local/etc/rules/local.rules:  <br/>
Note: "-i" specifies the interface name to monitor, yours will be different. Run "ip a" or "ifconfig" to your interface name <br/>
<img src="https://i.imgur.com/Wzrw7K5.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
 
<br />
If you don't have any errors in your .lua or .rules files, the test is successful and you will see Snort version and that monitring started as well : <br/>
<img src="https://i.imgur.com/dix6wJd.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />

<h2>3 ways I found to add additional rule files: </h2>


<p>1) go to the snort.lua file
at line 170 (the "ips" part, don't forget the 4 spaces before "include" and the comma after include
    include = "/path/to/rulesfile1.rules",
    include = "/path/to/rulesfile2.rules",</p>

    
<p>2) Within the command itself by specifying multiple rules files using the "-R" option </p><br/>
 sudo snort -c /usr/local/etc/snort/snort.lua --plugin-path /usr/local/etc/so_rules/ -i ens33 -A alert_fast -R /usr/local/etc/rules/rulefile1.rules -R /usr/local/etc/rules/rulefile2.rules -R /usr/local/etc/rules/rulefile3.rules -s 65535 -k none</p>

<p>3) go to the pulledpork3.conf
Search for: 
# Local Rules files
# Specify local rules files, comma-separated
local_rules = /usr/local/etc/rules/local.rules, /usr/local/etc/rules/local2.rules, /usr/local/etc/rules/local3.rules </p>
 
 
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
