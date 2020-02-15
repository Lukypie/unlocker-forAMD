+-----------------------------------------------------------------------------+
| IMPORTANT:   ONLY FOR VMware Workstation 15.1.0                             |
| ==========                                                                  |
|                                                                             |
| Don't remove files after installation!!!                                    |
|                                                                             |
+-----------------------------------------------------------------------------+
--Operation confirmed with--
AMD CPU
Windows 10, 64-bit  (Build 18363) 10.0.18363
macOS Mojave 10.14
--------------------

--How To--
1. Install VMware Workstation first.
2. Extract files to any folder.

3. Windows
Explorer right click on the command file and select "Run as administrator".

win-install.cmd   - patches VMware
win-uninstall.cmd - restores VMware
--------------------
3. Linux
On Linux you will need to be either root or use sudo to run the scripts.
You may need to ensure the Linux scripts have execute permissions
by running chmod +x against the 2 files.

lnx-install.sh   - patches VMware
lnx-uninstall.sh - restores VMware
--------------------

4. restart the PC.
Create a Virtual machine on VMware.

5. Editing the VMX File.
If you did not specify location, look in Documents\virtual machines\
Right click on the VMX file and choose "Open with". Choose "More Apps".
From the list of apps that will be seen, choose "Notepad" and press Enter.
---For Intel CPU---
At the bottom add the code:

smc.version = "0"

---For AMD CPU---
Change the code:

virtualHW.version = "10"

&
Add the code:

smc.version = "0"
cpuid.0.eax = "0000:0000:0000:0000:0000:0000:0000:1011"
cpuid.0.ebx = "0111:0101:0110:1110:0110:0101:0100:0111"
cpuid.0.ecx = "0110:1100:0110:0101:0111:0100:0110:1110"
cpuid.0.edx = "0100:1001:0110:0101:0110:1110:0110:1001"
cpuid.1.eax = "0000:0000:0000:0001:0000:0110:0111:0001"
cpuid.1.ebx = "0000:0010:0000:0001:0000:1000:0000:0000"
cpuid.1.ecx = "1000:0010:1001:1000:0010:0010:0000:0011"
cpuid.1.edx = "0000:1111:1010:1011:1111:1011:1111:1111"
featureCompat.enable = "FALSE"

Save the changes.
