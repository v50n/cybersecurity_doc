---
description: >-
  NTLM (Windows New Technology LAN Manager) is considered an outdated protocol.
  As such, its benefits — when compared to a more modern solution, such as
  Kerberos — are limited.
---

# NTLM authentification protocol

### What is NTLM ?&#x20;

NTLM (Windows New Technology LAN Manager) are used in Microsoft system to authenticate user **before Windows 2000**. NTLM is a single sign on (SSO) tool that work with the challenge-response mechanism.&#x20;

NTLM has been replaced by Kerberos as the default authentification protocol in Windows 2000.&#x20;

### Why still use NTLM ?

NTLM is still maintained in all Windows systems for compatibility purposes between older clients and servers (Example Windows 95,98,NT). OR if the kerberos fails to authenticate the user, the system will use NTLM

### The NTLM protocol's inconvenients :&#x20;

* Support <mark style="color:red;">**only**</mark> <mark style="color:red;"></mark><mark style="color:red;">Single</mark> Authentification
* Security vulnerabilities: object of 2 mode attacks : <mark style="color:red;">pass-the-hash</mark> and <mark style="color:red;">bruteforce</mark>
* Some <mark style="color:red;">outdated</mark> cryptography

### Some hash method used in NTLM authentification

#### NTLM

Example:&#x20;

<mark style="background-color:green;">Rachel:500:aad3c435b514a4eeaad3b935b51304fe:e46b9e548fa0d122de7f59fb6d48eaa2:::</mark>

* Rachel : Username
* 500 : Relative Identifier (RID)
* aad3c435b514a4eeaad3b935b51304fe : LM Hash
* e46b9e548fa0d122de7f59fb6d48eaa2 : NT hash: This hash can be cracked (depending on the length/strength of the password) OR used for a <mark style="color:red;">pass-the-hash</mark> attack.&#x20;
  * Exemple: crackmapexec smb IP -u rachel -H e46b9e548fa0d122de7f59fb6d48eaa2

#### NTLMv1

Upgrade version of NTLM. These hash can <mark style="color:red;">NOT</mark> be used for <mark style="color:red;">pass-the-hash</mark>

<mark style="background-color:green;">it.u4-netntlm::kNS:338d08f8e26de93300000000000000000000000000000000:9526fb8c23a90751cdd619b6cea564742e1e4bf33006ba41:cb8086049ec4736c</mark>

But we can <mark style="color:red;">bruteforce</mark> this hash

#### NTLMv2

Harder to bruteforce than NTLMv2.&#x20;

<mark style="background-color:green;">admin::N46iSNekpT:08ca45b7d7ea58ee:88dcbe4446168966a153a0064958dac6:5c7830315c7830310000000000000b45c67103d07d7b95acd12ffa11230e0000000052920b85f78d013c31cdb3b92f5d765c783030</mark>

#### Domain Cached Credentials (MSCache2)

&#x20;Example: <mark style="background-color:green;">$DCC2$10240#bjones#e4e938d12fe5974dc42a90120bd9c90f</mark>

All NTLM authentification protocol need to communicate with DC (Domain Controller). OR The MSCache2 or v1 **don’t need access to the network and don’t need to communicate with a domain controller (DC)** to authentification (for somes reason of technical issue)

* The MSCache stores **by default the last 10 hashes** for any domain users that successfully log into the machine in a registry key:  <mark style="background-color:orange;">HKEY\_LOCAL\_MACHINE\SECURITY\Cache</mark>.
* These hashes <mark style="color:red;">CANNOT be used in pass-the-hash</mark> attacks.&#x20;
* The hash is <mark style="color:red;">very slow to crack</mark>, even when using an extremely powerful GPU.

\
\
