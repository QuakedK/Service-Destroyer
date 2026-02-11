# Service Destroyer
Service Destroyer is specifically designed to disable system services, it doesn't target debloating windows like [Oneclick](https://github.com/QuakedK/Oneclick) or using NSudo to disable additional services like [Process Destroyer](https://github.com/QuakedK/Process-Destroyer). Meaning it may not be as effective as Oneclick or Process Destroyer, however it disables as much services as possible before reaching that absurd level. You can find additional info here -> [Extra Info](https://github.com/QuakedK/Service-Destroyer#4-extra-info)

<img width="978" height="512" alt="image" src="https://github.com/user-attachments/assets/ee9670e8-1d80-4210-9b44-aa7b5c441c31" />

![GitHub Release Downloads](https://img.shields.io/github/downloads/QuakedK/Service-Destroyer/total)

# #1 Usage
> [!NOTE]
> Service Destroyer provides full support for Windows 11, results may differ on older windows versions.

[Service Destroyer](https://github.com/QuakedK/Service-Destroyer/releases/download/WinServiceDisabler/Service-Destroyer-V1.4.bat) | 
The **Regular Version** disables all services, preventing a tons of services from automatically starting, this a great utility for those who simply want to target services! However because a ton of services are disabled, features and functionality is obviously lost. Please check and read the [Unsupported Features](https://github.com/QuakedK/Service-Destroyer/blob/main/Unsupported%20Features.md) and [Fixes](https://github.com/QuakedK/Service-Destroyer/blob/main/Fixes.md) before running the regular version of Service Destroyer.

[Service Destroyer Lite](https://github.com/QuakedK/Service-Destroyer/releases/download/WinServiceDisabler/Service-Destroyer-Lite-V1.4.bat) |
The **Lite Version** sets all services to manual preventing most services from automatically starting. This a great and simple this is a great alternative for those who don't want to lose functionality or deal with unsupport features.

1. Download and choose your [Service Destroyer](https://github.com/QuakedK/Service-Destroyer/releases/tag/WinServiceDisabler) version.
2. Right-click & run it as admin!

# #2 Revert
Note: If you created a Restore Point you can just use that <3

**Reg Backup**
1. Open CMD and paste the following then restart.
```bat
:: Revert Services.
reg import "C:\Service Destroyer\Reg Backup\ServicesBackup.reg"

:: Revert SvcHostThreshold.
reg add "HKLM\SYSTEM\CurrentControlSet\Control" /v SvcHostSplitThresholdInKB /t REG_DWORD /d 3670016 /f
```
> [!NOTE]
> The reg import command will provide an error, but thats because the Service Destroyer backs up all of the services keys.
> You won't have sufficient to restore some of the keys hence the error, but the services the program disabled can be restored without problem.
> Simply ignore the error as the keys you care about should've imported/reverted back to normal!

---

# #3 Results
The following test Compares Stock vs [Service Destroyer](https://github.com/QuakedK/Service-Destroyer/releases/download/WindowsServiceDisabler/Service-Destroyer-V1.1.bat) vs [Service Destroyer Lite](https://github.com/QuakedK/Service-Destroyer/releases/download/WindowsServiceDisabler/Service-Destroyer-Lite-V1.1.bat) on 24H2, after idling for 5 mins, having all startup apps disabled and but other Microsoft Bloat is still present.

<img width="2290" height="580" alt="New Project (2)" src="https://github.com/user-attachments/assets/f8cdf2cf-c087-4d95-a2d8-2cd124b3180f" />

# #4 Extra Info

**Services that didn't make the cut**: Lean more here → [Services Docs](https://github.com/QuakedK/Scripting-Station/blob/main/System%20Docs/Services.md)
```
1. Udk User Service.
Udk User Service slows down searching to a horrible degree, therefore left it's unchanged.

2. Time Broker Service.
When TimeBokerSvc is disabled Task Scheduler breaks, therefore left it's unchanged.

3. CNG Key Isolation Service
When KeyIso is disabled on a Online/Micsoft install of windows it gives PIN unavailable issue. Therefore it's left unchanged!

4. Microsoft Passport Service
When NgcSvc is disabled on a Online/Micsoft install of windows it gives a blank logon. Therefore it's left unchanged!

5. Microsoft Passport Container Service
When NgcCtnrSvc is disabled on a Online/Micsoft install of windows it gives a blank logon. Therefore it's left unchanged!

6. Application Information
When Appinfo is can't request admin permissions meaning you can't open apps that request administrator.
However the work around was just to disable UAC but some people will enable it cauing issues

7. DNS Client
If the DNS Client Service is stopped or disabled, on windows 11 24H2+ and 23H2 via Cumulative Updates then ethernet won't work.

8. Other Services...
Service Destroyer does not use NSudo so for services that need trusted installer privileges to be disabled aren't touched.
```

**Cryptographic Service**:
```
CryptSvc checks digital signatures of Windows files, manages root certificates, etc.
Windows protects this service with WRP (Windows Resource Protection), so it can’t easily be removed or disabled.
However it can be deleted in the registry, just make sure to backup the service!

CryptSvc appears to appears to cause, issues with certain Anti-Cheats. Hence on why it was removed from Service Destroyer.

:: Backup CryptSvc
mkdir "C:\CryptSvc"
reg export "HKLM\System\CurrentControlSet\Services\CryptSvc" "C:\CryptSvc\CryptSvcBackup.reg" /y

:: Delete CryptSvc
reg delete "HKLM\System\CurrentControlSet\Services\CryptSvc" /f

:: Revert/Restore CryptSvc
reg import "C:\CryptSvc\CryptSvcBackup.reg"
```

**Newer Services yet to be added**:
```
McmSvc - Mobile Connectivity Management Service
wuqisvc - Microsoft Usage and Quality Insights
midisrv - Windows MIDI Service 
```
 

