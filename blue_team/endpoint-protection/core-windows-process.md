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

<figure><img src="../.gitbook/assets/image.png" alt=""><figcaption></figcaption></figure>

What is anormal ?&#x20;

Not running in session 0, have a parent process, have multiple instance, PID !== 4

## smss.exe (system > smss.exe)

smss.exe is know as **Windows Session Manager**. This process is responsible for creating new session.&#x20;

