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

Repository name: SOC Lab Tools

<br>

Tools included:

(1) TLSKeyLogConfigurator.exe
(2) WindowsDefenderDisabler.exe
(3) WindowsDefenderEnabler.exe

<br>

Summary:

-----------------------------------------
TLSKeyLogConfigurator.exe
-----------------------------------------

The application performs the following functions:

(1) runs as a console application that performs user-level TLS key logging configuration and Wireshark preference updates; it is recommended to run the tool as an administrator to ensure successful execution policy adjustment for the current process;

(2) automates the setup of TLS key logging on Windows by creating a dedicated key log directory and file and configuring the SSLKEYLOGFILE user environment variable;

(3) updates Wireshark preferences to enable TLS session decryption using the configured key log file;

(4) provides a detailed status view showing Wireshark installation detection, key log file existence and size (bytes, KB, MB), environment variable state (user and session), and Wireshark TLS configuration status;

(5) supports safe configuration (no overwrite) and forced configuration modes, with optional backup creation of existing key log files and graceful handling of locked files;

(6) logs all actions to a transcript file stored on the user's desktop, enabling auditing and repeatability in forensic and SOC training environments.

-------------------------------------------
WindowsDefenderDisabler.exe
-------------------------------------------

The application performs the following functions:

(1) runs as a Windows utility intended for isolated lab environments and requires administrator privileges;

(2) disables Windows Defender by applying policy-level registry changes affecting 9 functional protection components, including real-time monitoring, behavior monitoring, cloud reporting, scanning features, and exploit guard controls;

(3) disables 7 Defender-related services and drivers by modifying their startup configuration at the system level;

(4) ensures persistence of the disabled state by creating and executing a scheduled task running as SYSTEM with multiple triggers, including system boot, user logon, and periodic execution, to ensure Windows Defender remains disabled and does not automatically re-enable itself over time;

(5) copies itself to a fixed system location and executes from there to ensure consistent task execution;

(6) appends a single timestamped entry per execution to a shared log file, providing a simple audit trail of Defender disable operations;

(7) displays an informational pop-up notification only on first execution when the scheduled task is created.

-------------------------------------------
WindowsDefenderEnabler.exe
-------------------------------------------

The application performs the following functions:

(1) runs as a Windows utility intended for restoring Windows Defender functionality in lab environments and requires administrator privileges;

(2) removes policy-level registry values used to disable Defender functional protection components;

(3) restores startup configuration for Defender-related services and drivers, re-enabling them to their default automatic state;

(4) deletes the scheduled task responsible for enforcing Defender disable persistence;

(5) appends a single timestamped entry per execution to the same shared log file used by the disabler, explicitly recording that Windows Defender was enabled and maintaining continuity of auditing;

(6) displays an informational pop-up notification only when the disabling scheduled task existed and was successfully removed.

-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
