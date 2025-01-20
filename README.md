<h1>Snort 3.0 Setup Tips</h1>

<p>Follow this official guide from Snort's website</p>
<b></b>
<a href="https://www.snort.org/documents/snort-3-1-18-0-on-ubuntu-18-20">Snort 3.1.18.0 on Ubuntu 18 & 20 Installation Guide</a>
<br />
<a href="https://docs.snort.org/welcome">Snort 3.0 Rule Writing Guide</a>
<br />
<a href="https://snort-org-site.s3.amazonaws.com/production/release_files/files/000/038/976/original/snort_user.html?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Credential=AKIAU7AK5ITMMOXGB2W5%2F20250120%2Fus-east-1%2Fs3%2Faws4_request&X-Amz-Date=20250120T164922Z&X-Amz-Expires=3600&X-Amz-SignedHeaders=host&X-Amz-Signature=464150f1085b259780f433d821100101aa6522158dfdc989e9a6f42918c6b41f">Snort 3.0 Manual</a>

<h2>Description</h2>

<h3>Project consists of:</h3>
<ol>
 <li>Best practices installation notes or administration notes where I noticed the documentation lacking</li>
 <li>3 Ways I found to run additional rule files</li>
 <li>Writing more advanced rules since most of the material online is so basic or based on Snort 2</li>
</ol>

<p><u>Important to note that</u> there's syntax difference between Snort 2 and Snort 3 rules when it comes to "," or ";" placement.</p>
<p>I included the .lua and .rules file as it's a functional configuration that works with Pullpork plugin</p>


<p>Note that there's a mistake in the documentation when setting up OpenAPPID. It's where you save the ODT file and hence, changing the path you specify for in the snort.lua file</p>

<h2>Setup is on Ubuntu</h2>

<p>I set up Snort 3 on Ubuntu, since not all distros have the same package list. You will run into many errors midway trying to set Snort 3 up on Kali if you are doing a manual build</p>

<h2>Best Practices Notes:</h2>

<p align="center">
<b>1.</b>Create a backup of the original .lua file and the .rules file, this way you revert back to originals or pervious verions in case your break the configuration with a change: <br/>
<img src="https://i.imgur.com/aiODyob.png" height="80%" width="80%" alt="configuration file backup"/>
<br />
<br />
<b>2.Test configuration and rules after every change</b></br>
sudo snort -c /usr/local/etc/snort/snort.lua --plugin-path /usr/local/etc/so_rules/ -i ens33 -A alert_fast -s 65535 -k none -d -R /usr/local/etc/rules/local.rules:  <br/>
Note: "-i" specifies the interface name to monitor, yours will be different. Run "ip a" or "ifconfig" to your interface name <br/>
<img src="https://i.imgur.com/Wzrw7K5.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
 
<br />
If you don't have any errors in your .lua or .rules files, the test is successful and you will see Snort version and that monitring started as well : <br/>
<img src="https://i.imgur.com/dix6wJd.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />

<h2>3 ways I found to add additional rule files: </h2>

<ol>
<li>
 go to the snort.lua file
at line 170 (the "ips" part, don't forget the 4 spaces before "include" and the comma after include
    include = "/path/to/rulesfile1.rules",
    include = "/path/to/rulesfile2.rules",</li>
<li>Within the command itself by specifying multiple rules files using the "-R" option<br/>
 sudo snort -c /usr/local/etc/snort/snort.lua --plugin-path /usr/local/etc/so_rules/ -i ens33 -A alert_fast -R /usr/local/etc/rules/rulefile1.rules -R /usr/local/etc/rules/rulefile2.rules -R /usr/local/etc/rules/rulefile3.rules -s 65535 -k none</li>
<li>go to the pulledpork3.conf
Search for: 
# Local Rules files
# Specify local rules files, comma-separated
local_rules = /usr/local/etc/rules/local.rules, /usr/local/etc/rules/local2.rules, /usr/local/etc/rules/local3.rules</li>
</ol>

    



 
 

<br />
The documentation, p. 24, specifies an incorrect location for the snort.lua file, <b>/usr/local/lib/</b>,  for the odt folder of OpenAppID.   <br/>
<p>The correct location is <b>'/usr/local/cisco/apps'</b>
<br>You will need to create the folders "cisco" & "apps"</br>
</p>

<br />
Rule writing depends on looking at captured PCAPs and writing rules to match them<br/>

<br />
<br />
Snort 3.0 Rule Writing Documenation is a great resource to refer to. I created rules based on its guidance and analyzing some malicious pcaps<br/>


<!--
 ```diff
- text in red
+ text in green
! text in orange
# text in gray
@@ text in purple (and bold)@@
```
--!>
