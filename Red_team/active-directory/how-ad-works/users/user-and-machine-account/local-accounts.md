# Local accounts

Local accounts are stored locally on a particular server or workstation.&#x20;

* <mark style="color:blue;">**Administrator**</mark>: SID: S-1-5-domain-500 : first account created with a Microsoft installation. It has full control in every resource on the system. It CANNOT be deleted or locked, but it can be disabled or renamed
* <mark style="color:blue;">**GUEST**</mark>: disabled by default. Recommended to disabled because it allow anonymous access to a host
* <mark style="color:blue;">**SYSTEM**</mark> : (or <mark style="color:blue;">**NT AUTHORITY\SYSTEM**</mark>) : default account installed and used by the OS to perform internal functions. Unlike root in linux, SYSTEM is a service account and does not run in the same context as regular user. It’s the highest permission level on a Windows host, it granted full control permissions to all files on a Windows.&#x20;
* <mark style="color:blue;">**Network Servic**</mark>e: a predefined local account used by the Service Control Manager (SCM) for running service.&#x20;
* Local Service:
