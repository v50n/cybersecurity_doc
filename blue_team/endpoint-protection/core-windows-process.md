# Core Windows process

All PID is random, except System

## Task manager

Can access via GUI or command line :&#x20;

* tasklist
* Get-Process
* ps
* wmic

## System

* PID is always 4
* Path : C:\Windows\system32\ntoskrnl.exe (NT OS Kernel)
* No parent process

<figure><img src="../.gitbook/assets/image (1).png" alt=""><figcaption></figcaption></figure>

What is anormal ?&#x20;

Not running in session 0, have a parent process, have multiple instance, PID !== 4

## smss.exe (system > smss.exe)

smss.exe is know as **Windows Session Manager**. This process is responsible for creating new session. It is a first user-mode process started by the kernel

* smss will starts csrss.exe and wininit.exe in Session 0. And csrss.exe and winlogon.exe for the session 1.&#x20;

<figure><img src="../.gitbook/assets/image.png" alt=""><figcaption></figcaption></figure>

* And all subsystem listed in the Required value of HKLM\System\CurrentControlSet\Control\Session Manager\Subsystems is also lauched
* Path: %SystemRoot%\System32\smss.exe
* Parent process : system

## Csrss.exe

* Client Server Runtime Process. This exe is the user-mode of Windows subsystem
* Path: %SystemRoot%\System32\csrss.exe
* Parent Process : Created by an instance of smss.exe

## wininit.exe

* Windows Initialization Process
* Is responsible for launching services.exe , lsass.exe, lsaiso.exe and another critical Windows process that run in the background
* Path : %SystemRoot%\System32\wininit.exe

### Wininit.exe > services.exe

* services.exe (Service Control Manager). Its primary responsible to handle the system services : loading services, interacting, start/stop the service. (sc start/stop)&#x20;
* Path : %SystemRoot%\System32\services.exe
* Parent : wininit.exe

### wininit.exe > services.exe > svchost.exe

* svchost (The Service Host) is responsible for hosting and managing Windows services.&#x20;
* Attacker can use svchost to install/call a malicious service (dll)
* Or attacker can create an exe similar to svchost.exe. Ex: scvhost.exe

### wininit.exe > lsass.exe

* lsass : Local Security Authority Subsystem Service
* This process verifies users logging on to Windows or server, handle password changes, create access token.&#x20;
* Attacker can use a tools lile mimikatz to dump credentials

## winlogon.exe

* The Windows Logon Process, tis responsible for handling the Secure Attention Sequence. It is the Ctr+Alt+DEL key
* This process is also responsible for loading the user profile. It loads the user's NTUSER.DAT into HKCU, and userinit.exe loads the user's shell.&#x20;

## explorer.exe

The process gives the user access to their folders and files.

Other functionnality like Start Menu and Taskbar



