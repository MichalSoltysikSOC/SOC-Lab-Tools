-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

Author: Michal Soltysik

Cybersecurity Analyst & Consultant | Forensics Examiner | SOC Trainer | Cyber Warfare Organizer

Official website: https://michalsoltysik.com/

LinkedIn: https://www.linkedin.com/in/michal-soltysik-ssh-soc/

Cybersecurity content: https://www.youtube.com/playlist?list=PL0RdRWQWldOAAKBqOVEutxKMP-a6CNoLY

Accredible: https://www.credential.net/profile/michalsoltysik/wallet

Credly: https://www.credly.com/users/michal-soltysik

Email: me@michalsoltysik.com

-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

Written in PowerShell (TLSKeyLogConfigurator, executed within the .NET-based Windows PowerShell runtime) and in C# (WindowsDefenderDisabler and WindowsDefenderEnabler, compiled against the .NET Framework 4.x).

All tools are compiled into .exe executable files with an MZ file header.

License: Free for personal and commercial use.

<br>

Tools included:

(1) TLSKeyLogConfigurator.exe
<br>
(2) WindowsDefenderDisabler.exe
<br>
(3) WindowsDefenderEnabler.exe

<br>

Summary:

-----------------------------------------
TLSKeyLogConfigurator.exe
-----------------------------------------

Important notice:

<br>

(1) This tool configures TLS key logging and Wireshark preferences, enabling decryption and inspection of encrypted web traffic for analysis purposes.

(2) When misused, TLS key logging may allow sensitive or private communications to be decrypted and inspected, potentially violating privacy, confidentiality, or organizational security policies.

(3) Execution of this tool must be explicitly approved by the system owner or an authorized administrator, and its use must comply with applicable laws, internal policies, and scope of authorization.

(4) This tool is intended exclusively for SOC labs, controlled test environments, and authorized forensic or training scenarios.

(5) Operation of this tool requires full understanding of its impact and full responsibility for its use, particularly when handling decrypted network traffic.

<br>
<br>

Prerequisite:

<br>

(1) Wireshark must be installed on the system for TLS traffic decryption to be usable; the tool configures TLS key logging and Wireshark preferences but does not install Wireshark itself.

<br>
<br>

The application performs the following functions:

<br>

(1) runs as a console application that performs user-level TLS key logging configuration and Wireshark preference updates; it is recommended to run the tool as an administrator to ensure successful execution policy adjustment for the current process;

(2) automates the setup of TLS key logging on Windows by creating a dedicated key log directory and file and configuring the SSLKEYLOGFILE user environment variable;

(3) updates Wireshark preferences to enable TLS session decryption using the configured key log file;

(4) provides a detailed status view showing Wireshark installation detection, key log file existence and size (bytes, KB, MB), environment variable state (user and session), and Wireshark TLS configuration status;

(5) supports safe configuration (no overwrite) and forced configuration modes, with optional backup creation of existing key log files and graceful handling of locked files;

(6) logs all actions to a transcript file stored on the user's desktop, enabling auditing and repeatability in forensic and SOC training environments.

-------------------------------------------
WindowsDefenderDisabler.exe
-------------------------------------------

Important notice:

<br>

(1) This tool modifies security-critical Windows Defender configuration by applying registry- and service-level enforcement intended exclusively for isolated SOC labs and controlled test environments.

(2) Improper use in a production environment, enterprise network, or unmanaged system may significantly reduce system security, expose the host to malware, or violate organizational security policies.

(3) Execution of this tool must be explicitly approved by the system owner or an authorized administrator. Use on systems without proper authorization or outside of controlled testing scenarios is strongly discouraged.

(4) Operation of this tool requires full understanding of its impact and full responsibility for its use.

(5) This tool must never be deployed on production systems, end-user workstations, or environments where security controls are required to remain active.

<br>
<br>

The application performs the following functions:

<br>

(1) runs as a Windows utility intended for isolated lab environments and requires administrator privileges;

(2) disables Windows Defender by applying policy-level registry changes affecting 9 functional protection components, including real-time monitoring, behavior monitoring, cloud reporting, scanning features, and exploit guard controls;

(3) disables 7 Defender-related services and drivers by modifying their startup configuration at the system level;

(4) ensures persistence of the disabled state by creating and executing a scheduled task running as SYSTEM with multiple triggers, including system boot, user logon, and periodic execution, to ensure Windows Defender remains disabled and does not automatically re-enable itself over time;

(5) copies itself to a fixed system location and executes from there to ensure consistent task execution;

(6) appends a single timestamped entry on each execution, including executions at system boot, at user logon, and multiple times per day (separate time triggers - effectively hourly), to a shared log file, recording Windows Defender disable operations and providing a simple audit trail;

(7) displays an informational pop-up notification only on first execution when the scheduled task is created.

-------------------------------------------
WindowsDefenderEnabler.exe
-------------------------------------------

The application performs the following functions:

<br>

(1) runs as a Windows utility intended for restoring Windows Defender functionality in lab environments and requires administrator privileges;

(2) removes policy-level registry values used to disable Defender functional protection components;

(3) restores startup configuration for Defender-related services and drivers, re-enabling them to their default automatic state;

(4) deletes the scheduled task responsible for enforcing Defender disable persistence;

(5) appends a single timestamped entry per execution to the same shared log file used by the disabler, explicitly recording that Windows Defender was enabled and maintaining continuity of auditing;

(6) displays an informational pop-up notification only when the disabling scheduled task existed and was successfully removed.

-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
