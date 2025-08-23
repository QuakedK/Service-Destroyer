# Service Destroyer
Service Destroyer is specifically designed to disable system services, it doesn't target debloating windows like [Oneclick](https://github.com/QuakedK/Oneclick) or using NSudo to disable additional services like [Process Destroyer](https://github.com/QuakedK/Process-Destroyer). Meaning it may not be as effective as Oneclick or Process Destroyer, however it disables as much services as possible before reaching that absurd level. You can find additional info here -> [Extra Info](https://github.com/QuakedK/Service-Destroyer/edit/main/README.md#4-extra-info)

<img width="978" height="512" alt="image" src="https://github.com/user-attachments/assets/ee9670e8-1d80-4210-9b44-aa7b5c441c31" />

![GitHub Release Downloads](https://img.shields.io/github/downloads/QuakedK/Service-Destroyer/total)

# #1 Usage

[Service Destroyer](https://github.com/QuakedK/Service-Destroyer/releases/download/WindowsServiceDisabler/Service-Destroyer-V1.1.bat) | 
The **Regular Version** disables all services, preventing a tons of services from automatically starting, this a great utility for those who simply want to target services! However because a ton of services are disabled, features and functionality is obviously lost. Please Check and read the [Unsupported Features](https://github.com/QuakedK/Service-Destroyer/blob/main/Unsupported%20Features.md).

[Service Destroyer Lite](https://github.com/QuakedK/Service-Destroyer/releases/download/WindowsServiceDisabler/Service-Destroyer-Lite-V1.1.bat) |
The **Lite Version** sets all services to manual preventing most services from automatically starting. This a great and simple this is a great alternative for those who don't want to lose functionality or deal with unsupport features.

1. Download and choose your [Service Destroyer](https://github.com/QuakedK/Service-Destroyer/releases/tag/WindowsServiceDisabler) version.
2. Right-click & run it as admin!

# #2 Revert
Note: If you created a Restore Point you can just use that <3

1. Open CMD and Paste the following.
```bat
:: Revert Services.
reg import "C:\Service Destroyer\Reg Backup\ServicesBackup.reg"

:: Revert SvcHostThreshold.
reg add "HKLM\SYSTEM\CurrentControlSet\Control" /v SvcHostSplitThresholdInKB /t REG_DWORD /d 3670016 /f
```

# #3 Results
The following test Compares Stock vs [Service Destroyer](https://github.com/QuakedK/Service-Destroyer/releases/download/WindowsServiceDisabler/Service-Destroyer-V1.1.bat) vs [Service Destroyer Lite](https://github.com/QuakedK/Service-Destroyer/releases/download/WindowsServiceDisabler/Service-Destroyer-Lite-V1.1.bat)on 24H2, after idling for 5 mins, having all startup apps disabled and but bloat other Microsoft Bloat is still present.

<img width="2290" height="580" alt="New Project" src="https://github.com/user-attachments/assets/d8c9d982-ffeb-4482-90c4-4a8c0e8e7d03" />

# #4 Extra Info

**Services that didn't make the cut**:
```
1. Udk User Service.
Udk User Service slows down searching to a horrible degree, therefore left it's unchanged.

2. Time Broker Service.
When TimeBokerSvc is disabled Task Scheduler breaks, therefore left it's unchanged.
```

**Windows Update Services**:
```
The following update services get deleted instead of solely being removed since, they tend to reenable themselves.

1. Windows Update Medic Service. - (WaaSMedicSvc)
2. Windows Update. - (wuauserv)
3. Update Orchestrator. - (UsoSvc)
```

**Application Information Service**:

```
Appinfo Service is responsible for facilitating elevated privilege requests, meaning it allows apps to run as an admin.
If disabled, apps can't request admin permissions meaning you can't open apps that request administrator.
However disabling Uac/User Account Control, allows you to get away with disabling AppInfo.

:: UAC Disable.
reg add "HKLM\SOFTWARE\Microsoft\Windows\CurrentVersion\Policies\System" /f /v EnableLUA /t REG_DWORD /d 0

:: UAC Enable.
reg add "HKLM\SOFTWARE\Microsoft\Windows\CurrentVersion\Policies\System" /f /v EnableLUA /t REG_DWORD /d 1
```

**Cryptographic Service**:
```
CryptSvc checks digital signatures of Windows files, manages root certificates, etc.
Windows protects this service with WRP (Windows Resource Protection), so it can’t easily be removed or disabled.
However deleting in the registry works!

:: Delete CryptSvc
reg delete "HKLM\System\CurrentControlSet\Services\CryptSvc" /f
```
 

