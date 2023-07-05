# Other Project
For QEMU ANTIDECTION, see https://github.com/zhaodice/qemu-anti-detection

# Proxmox VE(PVE 7.3-3) Anti Detection
 | Type       | Engine | Bypass |
 |------------|--------|--------|
 | AntiCheat | Mhyprot | ☑️   |
 | AntiCheat | Anti Cheat Expert(ACE) | ☑️   |
 | AntiCheat | Easy Anti Cheat(EAC) | ☑️   | 
 | AntiCheat | nProtect GameGuard(NP) | ☑️   | 
 | AntiCheat | Vanguard | ‼️(1: Incorrect function) | 
 | AntiCheat | Roblex | ‼️(The application encountered an unrecoverable error) | 
 | AntiCheat | Gepard (https://durin-ro.com/download) | ‼️VM Code 7: Sorry, this application cannot run under virtual machine |
 | Encrypt | VMProtect | ☑️   | 
 | Encrypt | VProtect | ☑️   |  
 | Encrypt | Themida | ☑️   |  
 | Encrypt | Enigma Protector | ☑️   |  
 | Encrypt | Safegine Shielden | ☑️   |  

‼️ There are games cannot run under this environment but I am not sure whether qemu has been detected, because the game doesn't say "Virtual machine detected" specifically. 

And this game (https://durin-ro.com/download) uses a unknown detection ,shows "Sorry, this application cannot run under virtual machine"
If you have any clue, feel free to tell me :),
Issue : https://github.com/zhaodice/proxmox-ve-anti-detection/issues/2

Flaws :
```
[Wed Jul  5 17:58:18 2023] [*] TLS process attach callback  -> 0
[Wed Jul  5 17:58:18 2023] [*] TLS thread attach callback  -> 0
[Wed Jul  5 17:58:18 2023] [*] Checking IsDebuggerPresent API  -> 0
[Wed Jul  5 17:58:18 2023] [*] Checking PEB.BeingDebugged  -> 0
[Wed Jul  5 17:58:18 2023] [*] Checking CheckRemoteDebuggerPresent API  -> 0
[Wed Jul  5 17:58:18 2023] [*] Checking PEB.NtGlobalFlag  -> 0
[Wed Jul  5 17:58:18 2023] [*] Checking ProcessHeap.Flags  -> 0
[Wed Jul  5 17:58:18 2023] [*] Checking ProcessHeap.ForceFlags  -> 0
[Wed Jul  5 17:58:18 2023] [*] Checking Low Fragmentation Heap -> 0
[Wed Jul  5 17:58:18 2023] [*] Checking NtQueryInformationProcess with ProcessDebugPort  -> 0
[Wed Jul  5 17:58:18 2023] [*] Checking NtQueryInformationProcess with ProcessDebugFlags  -> 0
[Wed Jul  5 17:58:18 2023] [*] Checking NtQueryInformationProcess with ProcessDebugObject  -> 0
[Wed Jul  5 17:58:18 2023] [*] Checking WudfIsAnyDebuggerPresent API  -> 0
[Wed Jul  5 17:58:18 2023] [*] Checking WudfIsKernelDebuggerPresent API  -> 0
[Wed Jul  5 17:58:18 2023] [*] Checking WudfIsUserDebuggerPresent API  -> 0
[Wed Jul  5 17:58:18 2023] [*] Checking NtSetInformationThread with ThreadHideFromDebugger  -> 0
[Wed Jul  5 17:58:18 2023] [*] Checking CloseHandle with an invalide handle  -> 0
[Wed Jul  5 17:58:18 2023] [*] Checking UnhandledExcepFilterTest  -> 0
[Wed Jul  5 17:58:18 2023] [*] Checking OutputDebugString  -> 0
[Wed Jul  5 17:58:18 2023] [*] Checking Hardware Breakpoints  -> 0
[Wed Jul  5 17:58:18 2023] [*] Checking Software Breakpoints  -> 0
[Wed Jul  5 17:58:18 2023] [*] Checking Interupt 0x2d  -> 0
[Wed Jul  5 17:58:18 2023] [*] Checking Interupt 1  -> 0
[Wed Jul  5 17:58:18 2023] [*] Checking trap flag -> 0
[Wed Jul  5 17:58:18 2023] [*] Checking Memory Breakpoints PAGE GUARD  -> 0
[Wed Jul  5 17:58:18 2023] [*] Checking If Parent Process is explorer.exe  -> 0
[Wed Jul  5 17:58:18 2023] [*] Checking SeDebugPrivilege  -> 0
[Wed Jul  5 17:58:18 2023] [*] Checking NtQueryObject with ObjectTypeInformation  -> 0
[Wed Jul  5 17:58:18 2023] [*] Checking NtQueryObject with ObjectAllTypesInformation  -> 0
[Wed Jul  5 17:58:19 2023] [*] Checking NtYieldExecution  -> 1
[Wed Jul  5 17:58:19 2023] [*] Checking CloseHandle protected handle trick   -> 0
[Wed Jul  5 17:58:19 2023] [*] Checking NtQuerySystemInformation with SystemKernelDebuggerInformation   -> 0
[Wed Jul  5 17:58:19 2023] [*] Checking SharedUserData->KdDebuggerEnabled   -> 0
[Wed Jul  5 17:58:19 2023] [*] Checking if process is in a job   -> 0
[Wed Jul  5 17:58:19 2023] [*] Checking VirtualAlloc write watch (buffer only)  -> 0
[Wed Jul  5 17:58:19 2023] [*] Checking VirtualAlloc write watch (API calls)  -> 0
[Wed Jul  5 17:58:19 2023] [*] Checking VirtualAlloc write watch (IsDebuggerPresent)  -> 0
[Wed Jul  5 17:58:19 2023] [*] Checking VirtualAlloc write watch (code write)  -> 0
[Wed Jul  5 17:58:19 2023] [*] Checking for page exception breakpoints  -> 0
[Wed Jul  5 17:58:19 2023] [*] Checking for API hooks outside module bounds  -> 0
[Wed Jul  5 17:58:19 2023] [*] Enumerating modules with EnumProcessModulesEx [32-bit]  -> 0
[Wed Jul  5 17:58:19 2023] [*] Enumerating modules with EnumProcessModulesEx [64-bit]  -> 0
[Wed Jul  5 17:58:19 2023] [*] Enumerating modules with EnumProcessModulesEx [ALL]  -> 0
[Wed Jul  5 17:58:19 2023] [*] Enumerating modules with ToolHelp32  -> 0
[Wed Jul  5 17:58:19 2023] [*] Enumerating the process LDR via LdrEnumerateLoadedModules  -> 0
[Wed Jul  5 17:58:19 2023] [*] Enumerating the process LDR directly  -> 0
[Wed Jul  5 17:58:20 2023] [*] Walking process memory with GetModuleInformation  -> 0
[Wed Jul  5 17:58:20 2023] [*] Walking process memory for hidden modules  -> 0
[Wed Jul  5 17:58:20 2023] [*] Checking if process loaded modules contains: avghookx.dll  -> 0
[Wed Jul  5 17:58:20 2023] [*] Checking if process loaded modules contains: avghooka.dll  -> 0
[Wed Jul  5 17:58:20 2023] [*] Checking if process loaded modules contains: snxhk.dll  -> 0
[Wed Jul  5 17:58:20 2023] [*] Checking if process loaded modules contains: sbiedll.dll  -> 0
[Wed Jul  5 17:58:20 2023] [*] Checking if process loaded modules contains: dbghelp.dll  -> 0
[Wed Jul  5 17:58:20 2023] [*] Checking if process loaded modules contains: api_log.dll  -> 0
[Wed Jul  5 17:58:20 2023] [*] Checking if process loaded modules contains: dir_watch.dll  -> 0
[Wed Jul  5 17:58:20 2023] [*] Checking if process loaded modules contains: pstorec.dll  -> 0
[Wed Jul  5 17:58:20 2023] [*] Checking if process loaded modules contains: vmcheck.dll  -> 0
[Wed Jul  5 17:58:20 2023] [*] Checking if process loaded modules contains: wpespy.dll  -> 0
[Wed Jul  5 17:58:20 2023] [*] Checking if process loaded modules contains: cmdvrt64.dll  -> 0
[Wed Jul  5 17:58:20 2023] [*] Checking if process loaded modules contains: cmdvrt32.dll  -> 0
[Wed Jul  5 17:58:20 2023] [*] Checking if process file name contains: sample.exe  -> 0
[Wed Jul  5 17:58:20 2023] [*] Checking if process file name contains: bot.exe  -> 0
[Wed Jul  5 17:58:20 2023] [*] Checking if process file name contains: sandbox.exe  -> 0
[Wed Jul  5 17:58:20 2023] [*] Checking if process file name contains: malware.exe  -> 0
[Wed Jul  5 17:58:20 2023] [*] Checking if process file name contains: test.exe  -> 0
[Wed Jul  5 17:58:20 2023] [*] Checking if process file name contains: klavme.exe  -> 0
[Wed Jul  5 17:58:20 2023] [*] Checking if process file name contains: myapp.exe  -> 0
[Wed Jul  5 17:58:20 2023] [*] Checking if process file name contains: testapp.exe  -> 0
[Wed Jul  5 17:58:20 2023] [*] Checking if process file name looks like a hash: al-khaser  -> 0
[Wed Jul  5 17:58:20 2023] [*] Checking if username matches : CurrentUser  -> 0
[Wed Jul  5 17:58:20 2023] [*] Checking if username matches : Sandbox  -> 0
[Wed Jul  5 17:58:20 2023] [*] Checking if username matches : Emily  -> 0
[Wed Jul  5 17:58:20 2023] [*] Checking if username matches : HAPUBWS  -> 0
[Wed Jul  5 17:58:20 2023] [*] Checking if username matches : Hong Lee  -> 0
[Wed Jul  5 17:58:20 2023] [*] Checking if username matches : IT-ADMIN  -> 0
[Wed Jul  5 17:58:20 2023] [*] Checking if username matches : Johnson  -> 0
[Wed Jul  5 17:58:20 2023] [*] Checking if username matches : Miller  -> 0
[Wed Jul  5 17:58:20 2023] [*] Checking if username matches : milozs  -> 0
[Wed Jul  5 17:58:20 2023] [*] Checking if username matches : Peter Wilson  -> 0
[Wed Jul  5 17:58:20 2023] [*] Checking if username matches : timmy  -> 0
[Wed Jul  5 17:58:20 2023] [*] Checking if username matches : user  -> 0
[Wed Jul  5 17:58:20 2023] [*] Checking if username matches : sand box  -> 0
[Wed Jul  5 17:58:20 2023] [*] Checking if username matches : malware  -> 0
[Wed Jul  5 17:58:20 2023] [*] Checking if username matches : maltest  -> 0
[Wed Jul  5 17:58:20 2023] [*] Checking if username matches : test user  -> 0
[Wed Jul  5 17:58:20 2023] [*] Checking if username matches : virus  -> 0
[Wed Jul  5 17:58:20 2023] [*] Checking if username matches : John Doe  -> 0
[Wed Jul  5 17:58:20 2023] [*] Checking if hostname matches : SANDBOX  -> 0
[Wed Jul  5 17:58:20 2023] [*] Checking if hostname matches : 7SILVIA  -> 0
[Wed Jul  5 17:58:20 2023] [*] Checking if hostname matches : HANSPETER-PC  -> 0
[Wed Jul  5 17:58:20 2023] [*] Checking if hostname matches : JOHN-PC  -> 0
[Wed Jul  5 17:58:20 2023] [*] Checking if hostname matches : MUELLER-PC  -> 0
[Wed Jul  5 17:58:20 2023] [*] Checking if hostname matches : WIN7-TRAPS  -> 0
[Wed Jul  5 17:58:20 2023] [*] Checking if hostname matches : FORTINET  -> 0
[Wed Jul  5 17:58:20 2023] [*] Checking if hostname matches : TEQUILABOOMBOOM  -> 0
[Wed Jul  5 17:58:20 2023] [*] Checking whether username is 'Wilber' and NetBIOS name starts with 'SC' or 'SW'  -> 0
[Wed Jul  5 17:58:20 2023] [*] Checking whether username is 'admin' and NetBIOS name is 'SystemIT'  -> 0
[Wed Jul  5 17:58:20 2023] [*] Checking whether username is 'admin' and DNS hostname is 'KLONE_X64-PC'  -> 0
[Wed Jul  5 17:58:20 2023] [*] Checking whether username is 'John' and two sandbox files exist  -> 0
[Wed Jul  5 17:58:20 2023] [*] Checking whether four known sandbox 'email' file paths exist  -> 0
[Wed Jul  5 17:58:20 2023] [*] Checking whether three known sandbox 'foobar' files exist  -> 0
[Wed Jul  5 17:58:20 2023] [*] Checking Number of processors in machine  -> 0
[Wed Jul  5 17:58:20 2023] [*] Checking Interupt Descriptor Table location  -> 0
[Wed Jul  5 17:58:20 2023] [*] Checking Local Descriptor Table location  -> 1
[Wed Jul  5 17:58:20 2023] [*] Checking Global Descriptor Table location  -> 0
[Wed Jul  5 17:58:20 2023] [*] Checking Store Task Register  -> 0
[Wed Jul  5 17:58:21 2023] [*] Checking Number of cores in machine using WMI  -> 0
[Wed Jul  5 17:58:21 2023] [*] Checking hard disk size using WMI  -> 1
[Wed Jul  5 17:58:21 2023] [*] Checking hard disk size using DeviceIoControl  -> 0
[Wed Jul  5 17:58:21 2023] [*] Checking SetupDi_diskdrive  -> 0
[Wed Jul  5 17:58:26 2023] [*] Checking mouse movement  -> 0
[Wed Jul  5 17:58:26 2023] [*] Checking lack of user input  -> 0
[Wed Jul  5 17:58:26 2023] [*] Checking memory space using GlobalMemoryStatusEx  -> 0
[Wed Jul  5 17:58:26 2023] [*] Checking disk size using GetDiskFreeSpaceEx  -> 1
[Wed Jul  5 17:58:26 2023] [*] Checking if CPU hypervisor field is set using cpuid(0x1) -> 0
[Wed Jul  5 17:58:26 2023] [*] Checking hypervisor vendor using cpuid(0x40000000) -> 0
[Wed Jul  5 17:59:26 2023] [*] Check if time has been accelerated  -> 0
[Wed Jul  5 17:59:26 2023] [*] VM Driver Services   -> 0
[Wed Jul  5 17:59:26 2023] [*] Checking SerialNumber from BIOS using WMI  -> 0
[Wed Jul  5 17:59:26 2023] [*] Checking Model from ComputerSystem using WMI  -> 0
[Wed Jul  5 17:59:26 2023] [*] Checking Manufacturer from ComputerSystem using WMI  -> 0
[Wed Jul  5 17:59:26 2023] [*] Checking Current Temperature using WMI  -> 0
[Wed Jul  5 17:59:27 2023] [*] Checking ProcessId using WMI  -> 0
[Wed Jul  5 17:59:27 2023] [*] Checking power capabilities  -> 0
[Wed Jul  5 17:59:27 2023] [*] Checking CPU fan using WMI  -> 1
[Wed Jul  5 17:59:27 2023] [*] Checking NtQueryLicenseValue with Kernel-VMDetection-Private  -> 0
[Wed Jul  5 17:59:27 2023] [*] Checking Win32_CacheMemory with WMI  -> 1
[Wed Jul  5 17:59:27 2023] [*] Checking Win32_PhysicalMemory with WMI  -> 0
[Wed Jul  5 17:59:28 2023] [*] Checking Win32_MemoryDevice with WMI  -> 1
[Wed Jul  5 17:59:28 2023] [*] Checking Win32_MemoryArray with WMI  -> 0
[Wed Jul  5 17:59:28 2023] [*] Checking Win32_VoltageProbe with WMI  -> 1
[Wed Jul  5 17:59:28 2023] [*] Checking Win32_PortConnector with WMI  -> 1
[Wed Jul  5 17:59:28 2023] [*] Checking Win32_SMBIOSMemory with WMI  -> 0
[Wed Jul  5 17:59:33 2023] [*] Checking ThermalZoneInfo performance counters with WMI  -> 1
[Wed Jul  5 17:59:33 2023] [*] Checking CIM_Memory with WMI  -> 1
[Wed Jul  5 17:59:33 2023] [*] Checking CIM_Sensor with WMI  -> 1
[Wed Jul  5 17:59:33 2023] [*] Checking CIM_NumericSensor with WMI  -> 1
[Wed Jul  5 17:59:33 2023] [*] Checking CIM_TemperatureSensor with WMI  -> 1
[Wed Jul  5 17:59:33 2023] [*] Checking CIM_VoltageSensor with WMI  -> 1
[Wed Jul  5 17:59:33 2023] [*] Checking CIM_PhysicalConnector with WMI  -> 1
[Wed Jul  5 17:59:33 2023] [*] Checking CIM_Slot with WMI  -> 1
[Wed Jul  5 17:59:33 2023] [*] Checking if Windows is Genuine  -> 0
[Wed Jul  5 17:59:33 2023] [*] Checking Services\Disk\Enum entries for VM strings  -> 0
[Wed Jul  5 17:59:33 2023] [*] Checking Enum\IDE and Enum\SCSI entries for VM strings  -> 0
[Wed Jul  5 17:59:33 2023] [*] Checking reg key HARDWARE\Description\System - Identifier is set to VBOX -> 0
[Wed Jul  5 17:59:33 2023] [*] Checking reg key HARDWARE\Description\System - SystemBiosVersion is set to VBOX -> 0
[Wed Jul  5 17:59:33 2023] [*] Checking reg key HARDWARE\Description\System - VideoBiosVersion is set to VIRTUALBOX -> 0
[Wed Jul  5 17:59:33 2023] [*] Checking reg key HARDWARE\Description\System - SystemBiosDate is set to 06/23/99 -> 0
[Wed Jul  5 17:59:33 2023] [*] Checking VirtualBox Guest Additions directory  -> 0
[Wed Jul  5 17:59:33 2023] [*] Checking file C:\Windows\System32\drivers\VBoxMouse.sys  -> 0
[Wed Jul  5 17:59:33 2023] [*] Checking file C:\Windows\System32\drivers\VBoxGuest.sys  -> 0
[Wed Jul  5 17:59:33 2023] [*] Checking file C:\Windows\System32\drivers\VBoxSF.sys  -> 0
[Wed Jul  5 17:59:33 2023] [*] Checking file C:\Windows\System32\drivers\VBoxVideo.sys  -> 0
[Wed Jul  5 17:59:33 2023] [*] Checking file C:\Windows\System32\vboxdisp.dll  -> 0
[Wed Jul  5 17:59:33 2023] [*] Checking file C:\Windows\System32\vboxhook.dll  -> 0
[Wed Jul  5 17:59:33 2023] [*] Checking file C:\Windows\System32\vboxmrxnp.dll  -> 0
[Wed Jul  5 17:59:33 2023] [*] Checking file C:\Windows\System32\vboxogl.dll  -> 0
[Wed Jul  5 17:59:33 2023] [*] Checking file C:\Windows\System32\vboxoglarrayspu.dll  -> 0
[Wed Jul  5 17:59:33 2023] [*] Checking file C:\Windows\System32\vboxoglcrutil.dll  -> 0
[Wed Jul  5 17:59:33 2023] [*] Checking file C:\Windows\System32\vboxoglerrorspu.dll  -> 0
[Wed Jul  5 17:59:33 2023] [*] Checking file C:\Windows\System32\vboxoglfeedbackspu.dll  -> 0
[Wed Jul  5 17:59:33 2023] [*] Checking file C:\Windows\System32\vboxoglpackspu.dll  -> 0
[Wed Jul  5 17:59:33 2023] [*] Checking file C:\Windows\System32\vboxoglpassthroughspu.dll  -> 0
[Wed Jul  5 17:59:33 2023] [*] Checking file C:\Windows\System32\vboxservice.exe  -> 0
[Wed Jul  5 17:59:33 2023] [*] Checking file C:\Windows\System32\vboxtray.exe  -> 0
[Wed Jul  5 17:59:33 2023] [*] Checking file C:\Windows\System32\VBoxControl.exe  -> 0
[Wed Jul  5 17:59:33 2023] [*] Checking reg key HARDWARE\ACPI\DSDT\VBOX__  -> 0
[Wed Jul  5 17:59:33 2023] [*] Checking reg key HARDWARE\ACPI\FADT\VBOX__  -> 0
[Wed Jul  5 17:59:33 2023] [*] Checking reg key HARDWARE\ACPI\RSDT\VBOX__  -> 0
[Wed Jul  5 17:59:33 2023] [*] Checking reg key SOFTWARE\Oracle\VirtualBox Guest Additions  -> 0
[Wed Jul  5 17:59:33 2023] [*] Checking reg key SYSTEM\ControlSet001\Services\VBoxGuest  -> 0
[Wed Jul  5 17:59:33 2023] [*] Checking reg key SYSTEM\ControlSet001\Services\VBoxMouse  -> 0
[Wed Jul  5 17:59:33 2023] [*] Checking reg key SYSTEM\ControlSet001\Services\VBoxService  -> 0
[Wed Jul  5 17:59:33 2023] [*] Checking reg key SYSTEM\ControlSet001\Services\VBoxSF  -> 0
[Wed Jul  5 17:59:33 2023] [*] Checking reg key SYSTEM\ControlSet001\Services\VBoxVideo  -> 0
[Wed Jul  5 17:59:33 2023] [*] Checking Mac Address start with 08:00:27  -> 0
[Wed Jul  5 17:59:33 2023] [*] Checking MAC address (Hybrid Analysis)  -> 0
[Wed Jul  5 17:59:33 2023] [*] Checking device \\.\VBoxMiniRdrDN  -> 0
[Wed Jul  5 17:59:33 2023] [*] Checking device \\.\VBoxGuest  -> 0
[Wed Jul  5 17:59:33 2023] [*] Checking device \\.\pipe\VBoxMiniRdDN  -> 0
[Wed Jul  5 17:59:33 2023] [*] Checking device \\.\VBoxTrayIPC  -> 0
[Wed Jul  5 17:59:33 2023] [*] Checking device \\.\pipe\VBoxTrayIPC  -> 0
[Wed Jul  5 17:59:33 2023] [*] Checking VBoxTrayToolWndClass / VBoxTrayToolWnd  -> 0
[Wed Jul  5 17:59:33 2023] [*] Checking VirtualBox Shared Folders network provider  -> 0
[Wed Jul  5 17:59:33 2023] [*] Checking VirtualBox process vboxservice.exe  -> 0
[Wed Jul  5 17:59:33 2023] [*] Checking VirtualBox process vboxtray.exe  -> 0
[Wed Jul  5 17:59:33 2023] [*] Checking Win32_PnPDevice DeviceId from WMI for VBox PCI device  -> 0
[Wed Jul  5 17:59:33 2023] [*] Checking Win32_PnPDevice Name from WMI for VBox controller hardware  -> 0
[Wed Jul  5 17:59:33 2023] [*] Checking Win32_PnPDevice Name from WMI for VBOX names  -> 0
[Wed Jul  5 17:59:33 2023] [*] Checking Win32_Bus from WMI  -> 0
[Wed Jul  5 17:59:33 2023] [*] Checking Win32_BaseBoard from WMI  -> 0
[Wed Jul  5 17:59:33 2023] [*] Checking MAC address from WMI  -> 0
[Wed Jul  5 17:59:33 2023] [*] Checking NTEventLog from WMI  -> 0
[Wed Jul  5 17:59:33 2023] [*] Checking SMBIOS firmware   -> 0
[Wed Jul  5 17:59:33 2023] [*] Checking ACPI tables   -> 0
[Wed Jul  5 17:59:33 2023] [*] Checking reg key HARDWARE\DEVICEMAP\Scsi\Scsi Port 0\Scsi Bus 0\Target Id 0\Logical Unit Id 0 -> 0
[Wed Jul  5 17:59:33 2023] [*] Checking reg key HARDWARE\DEVICEMAP\Scsi\Scsi Port 1\Scsi Bus 0\Target Id 0\Logical Unit Id 0 -> 0
[Wed Jul  5 17:59:33 2023] [*] Checking reg key HARDWARE\DEVICEMAP\Scsi\Scsi Port 2\Scsi Bus 0\Target Id 0\Logical Unit Id 0 -> 0
[Wed Jul  5 17:59:33 2023] [*] Checking reg key SYSTEM\ControlSet001\Control\SystemInformation -> 0
[Wed Jul  5 17:59:33 2023] [*] Checking reg key SYSTEM\ControlSet001\Control\SystemInformation -> 0
[Wed Jul  5 17:59:33 2023] [*] Checking reg key SOFTWARE\VMware, Inc.\VMware Tools  -> 0
[Wed Jul  5 17:59:33 2023] [*] Checking file C:\Windows\System32\drivers\vmnet.sys  -> 0
[Wed Jul  5 17:59:33 2023] [*] Checking file C:\Windows\System32\drivers\vmmouse.sys  -> 0
[Wed Jul  5 17:59:33 2023] [*] Checking file C:\Windows\System32\drivers\vmusb.sys  -> 0
[Wed Jul  5 17:59:33 2023] [*] Checking file C:\Windows\System32\drivers\vm3dmp.sys  -> 0
[Wed Jul  5 17:59:33 2023] [*] Checking file C:\Windows\System32\drivers\vmci.sys  -> 0
[Wed Jul  5 17:59:33 2023] [*] Checking file C:\Windows\System32\drivers\vmhgfs.sys  -> 0
[Wed Jul  5 17:59:33 2023] [*] Checking file C:\Windows\System32\drivers\vmmemctl.sys  -> 0
[Wed Jul  5 17:59:33 2023] [*] Checking file C:\Windows\System32\drivers\vmx86.sys  -> 0
[Wed Jul  5 17:59:33 2023] [*] Checking file C:\Windows\System32\drivers\vmrawdsk.sys  -> 0
[Wed Jul  5 17:59:33 2023] [*] Checking file C:\Windows\System32\drivers\vmusbmouse.sys  -> 0
[Wed Jul  5 17:59:33 2023] [*] Checking file C:\Windows\System32\drivers\vmkdb.sys  -> 0
[Wed Jul  5 17:59:33 2023] [*] Checking file C:\Windows\System32\drivers\vmnetuserif.sys  -> 0
[Wed Jul  5 17:59:33 2023] [*] Checking file C:\Windows\System32\drivers\vmnetadapter.sys  -> 0
[Wed Jul  5 17:59:33 2023] [*] Checking MAC starting with 00:05:69 -> 0
[Wed Jul  5 17:59:33 2023] [*] Checking MAC starting with 00:0c:29 -> 0
[Wed Jul  5 17:59:33 2023] [*] Checking MAC starting with 00:1C:14 -> 0
[Wed Jul  5 17:59:33 2023] [*] Checking MAC starting with 00:50:56 -> 0
[Wed Jul  5 17:59:33 2023] [*] Checking VMWare network adapter name  -> 0
[Wed Jul  5 17:59:33 2023] [*] Checking device \\.\HGFS  -> 0
[Wed Jul  5 17:59:33 2023] [*] Checking device \\.\vmci  -> 0
[Wed Jul  5 17:59:33 2023] [*] Checking VMWare directory  -> 0
[Wed Jul  5 17:59:33 2023] [*] Checking SMBIOS firmware   -> 0
[Wed Jul  5 17:59:33 2023] [*] Checking ACPI tables   -> 0
[Wed Jul  5 17:59:33 2023] [*] Checking Virtual PC processes VMSrvc.exe  -> 0
[Wed Jul  5 17:59:33 2023] [*] Checking Virtual PC processes VMUSrvc.exe  -> 0
[Wed Jul  5 17:59:33 2023] [*] Checking reg key SOFTWARE\Microsoft\Virtual Machine\Guest\Parameters  -> 0
[Wed Jul  5 17:59:33 2023] [*] Checking reg key HARDWARE\DEVICEMAP\Scsi\Scsi Port 0\Scsi Bus 0\Target Id 0\Logical Unit Id 0  -> 0
[Wed Jul  5 17:59:33 2023] [*] Checking reg key HARDWARE\Description\System  -> 0
[Wed Jul  5 17:59:33 2023] [*] Checking qemu processes qemu-ga.exe  -> 0
[Wed Jul  5 17:59:33 2023] [*] Checking SMBIOS firmware   -> 0
[Wed Jul  5 17:59:33 2023] [*] Checking ACPI tables   -> 0
[Wed Jul  5 17:59:33 2023] [*] Checking Citrix Xen process xenservice.exe -> 0
[Wed Jul  5 17:59:33 2023] [*] Checking Mac Address start with 08:16:3E  -> 0
[Wed Jul  5 17:59:33 2023] [*] Checking Wine via dll exports  -> 0
[Wed Jul  5 17:59:33 2023] [*] Checking reg key SOFTWARE\Wine  -> 0
[Wed Jul  5 17:59:33 2023] [*] Checking Parallels processes: prl_cc.exe -> 0
[Wed Jul  5 17:59:33 2023] [*] Checking Parallels processes: prl_tools.exe -> 0
[Wed Jul  5 17:59:33 2023] [*] Checking Mac Address start with 08:1C:42  -> 0
[Wed Jul  5 18:09:33 2023] [*] Performing a sleep using NtDelayExecution ... -> 0
[Wed Jul  5 18:19:34 2023] [*] Performing a sleep() in a loop ... -> 0
[Wed Jul  5 18:39:34 2023] [*] Delaying execution using SetTimer ... -> 0
[Wed Jul  5 18:39:34 2023] [*] Delaying execution using timeSetEvent ... -> 0
```

# Build deb(or download my release ,jump to install section.)

!!! Create Proxmox VE Virtual Machine as compile enviromnet. !!!

1.Login System


2.Remove the old:
```
mv /etc/apt/sources.list /etc/apt/sources.list.deleted
mv /etc/apt/sources.list.d/pve-enterprise.list /etc/apt/sources.list.d/pve-enterprise.list.deleted
```


3.Add follows into `/etc/apt/sources.list`
```
deb https://mirrors.ustc.edu.cn/debian/ bullseye main contrib non-free
deb https://mirrors.ustc.edu.cn/debian/ bullseye-updates main contrib non-free
deb https://mirrors.ustc.edu.cn/debian/ bullseye-backports main contrib non-free
deb https://mirrors.ustc.edu.cn/debian-security bullseye-security main contrib
#pve源
deb https://mirrors.ustc.edu.cn/proxmox/debian bullseye pve-no-subscription
#ceph源
deb https://mirrors.ustc.edu.cn/proxmox/debian/ceph-pacific bullseye main
#开发源，必须
deb https://mirrors.ustc.edu.cn/proxmox/debian/devel bullseye main
```


4.
(This patch is made at commit 93d558c1eef8f3ec76983cbe6848b0dc606ea5f1)
```
apt update
git clone git://git.proxmox.com/git/pve-qemu.git
cd pve-qemu
git reset --hard 93d558c1eef8f3ec76983cbe6848b0dc606ea5f1
apt install  devscripts
mk-build-deps --install
wget "https://github.com/zhaodice/proxmox-ve-anti-detecion/raw/main/001-anti-detection.patch" -O qemu/001-anti-detection.patch
```

5.

`nano debian/rules`

FIND LINE:

```
	# guest-agent is only required for guest systems
	./configure \
	--with-git-submodules=ignore \
	--docdir=/usr/share/doc/pve-qemu-kvm \
	--localstatedir=/var \
	--prefix=/usr \
	--sysconfdir=/etc \
	--target-list=$(ARCH)-softmmu,aarch64-softmmu \
	--with-suffix="kvm" \
	--with-pkgversion="${DEB_SOURCE}_${DEB_VERSION_UPSTREAM_REVISION}" \
	--audio-drv-list="alsa" \
	--datadir=/usr/share \
	--libexecdir=/usr/lib/kvm \
	--disable-capstone \
	--disable-gtk \
	--disable-guest-agent \
	--disable-guest-agent-msi \
	--disable-libnfs \
	--disable-libssh \
	--disable-sdl \
	--disable-smartcard \
	--disable-strip \
	--disable-xen \
	--enable-curl \
	--enable-docs \
	--enable-glusterfs \
	--enable-gnutls \
	--enable-libiscsi \
	--enable-libusb \
	--enable-linux-aio \
	--enable-linux-io-uring \
	--enable-numa \
	--enable-opengl \
	--enable-rbd \
	--enable-seccomp \
	--enable-slirp \
	--enable-spice \
	--enable-usb-redir \
	--enable-virglrenderer \
	--enable-virtfs \
	--enable-virtiofsd \
	--enable-zstd
```


Inject a line :

```
	# [Inject]Surprised Detector's Mother Fucker !!!
	patch -p1 < 001-anti-detection.patch
	
	# guest-agent is only required for guest systems
	...
```

6 Current folder is `git's root path`.
```
make clean
make
```

7.You will see a `ERROR` follows

```
dpkg-source: info: unapplying 001-anti-detection.patch
dpkg-source: error: diff pve-qemu-kvm-7.2.0/debian/patches/001-anti-detection.patch modifies file pve-qemu-kvm-7.2.0/subprojects/libvduse/standard-headers/linux/qemu_fw_cfg.h through a symlink: pve-qemu-kvm-7.2.0/subprojects/libvduse/standard-headers/linux
dpkg-buildpackage: error: dpkg-source --after-build . subprocess returned exit status 25
make: *** [Makefile:36: pve-qemu-kvm_7.2.0-8_amd64.deb] Error 25
```

Due to you edit the `rule` files to patch, so it cannot unapplying extra patch

but it is NO PROBLME, because you will see a patched deb file `pve-qemu-kvm_7.2.0-8_amd64.deb` !

# Install deb

copy `pve-qemu-kvm_7.2.0-8_amd64.deb` into your real PVE system.(to use this deb , you should install `librbd-dev=16.2.11-pve1` first)
```
apt install librbd-dev
dpkg -i pve-qemu-kvm_7.2.0-8_amd64.deb
```

# VM Show

`/etc/pve/qemu-server/100.conf`
```
args: -cpu host,+kvm_pv_unhalt,+kvm_pv_eoi,hv_spinlocks=0x1fff,hv_vapic,hv_time,hv_reset,hv_vpindex,hv_runtime,hv_relaxed,kvm=off,hv_vendor_id=intel,vmware-cpuid-freq=false,enforce=false,host-phys-bits=true,hypervisor=off -smbios type=0,version=UX305UA.201 -smbios type=1,manufacturer=ASUS,product=UX305UA,version=2021.1 -smbios type=2,manufacturer=Intel,version=2021.5,product='Intel i9-12900K' -smbios type=3,manufacturer=XBZJ -smbios type=17,manufacturer=KINGSTON,loc_pfx=DDR5,speed=4800,serial=114514,part=FF63 -smbios type=4,manufacturer=Intel,max-speed=4800,current-speed=4800
audio0: device=ich9-intel-hda,driver=none
balloon: 0
bios: ovmf
boot: order=sata0
cores: 12
cpu: host,flags=+pcid
efidisk0: local-lvm:vm-100-disk-0,efitype=4m,pre-enrolled-keys=1,size=4M
hostpci0: 0000:01:00,pcie=1,x-vga=1
machine: pc-q35-7.1
memory: 32768
meta: creation-qemu=7.1.0,ctime=1679627202
name: Windows11
net0: rtl8139=CA:09:F3:97:56:0B,bridge=vmbr0,firewall=1
numa: 1
ostype: win11
sata0: HugeSSD:100/vm-100-disk-1.qcow2,discard=on,size=64G,ssd=1
sata1: HugeHDD:100/vm-100-disk-0.qcow2,backup=0,size=128G
smbios1: uuid=24c326dd-3cec-48fc-bb9f-87aa3984e2c9,manufacturer=QVNVUw==,product=VVgzMDVVQQ==,version=MjAyMS4x,serial=MTI0NjY3,sku=MTM0NDY4,family=Ng==,base64=1
sockets: 1
tpmstate0: local-lvm:vm-100-disk-1,size=4M,version=v2.0
usb0: host=4e53:5406
usb1: host=040b:2000
vga: none
vmgenid: 020229e3-2cdb-4a91-8e77-1d04cf1f060f
```

![Screenshot_20230329_124628](https://user-images.githubusercontent.com/63996691/228429821-443a3a9f-8d24-4712-9760-bbfb1f10aa8d.png)
