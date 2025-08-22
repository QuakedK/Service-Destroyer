# Service Destroyer
Service Destroyer is specifically designed to disable system services, it doesn't target debloating windows like [Oneclick](https://github.com/QuakedK/Oneclick) or using NSudo to disable additional services like [Process Destroyer](https://github.com/QuakedK/Process-Destroyer). Meaning it may not be as effective as Oneclick or Process Destroyer, however it disables as much services as possible before reaching that absurd level. You can find additional info here -> [Extra Info](https://github.com/QuakedK/Service-Destroyer/edit/main/README.md#4-extra-info)

<img width="978" height="512" alt="image" src="https://github.com/user-attachments/assets/ee9670e8-1d80-4210-9b44-aa7b5c441c31" />

![GitHub Release Downloads](https://img.shields.io/github/downloads/QuakedK/Service-Destroyer/total)

# #1 Usage

# #2 Usage

# #3 Results
The following test was done on 24H2, after idling for 5 mins, having 0 startup apps enabled and no bloat removed.

<img width="1540" height="584" alt="New Project (1)" src="https://github.com/user-attachments/assets/4e8c7a90-3b7f-42ef-9b0e-9a8b6c0f8604" />

# #4 Extra Info

**Services that didn't make the cut:**
```
1. Udk User Service.
Udk User Service slows down searching to a horrible degree, therefore left it's unchanged.

2. Time Broker Service.
When TimeBokerSvc is disabled Task Scheduler breaks, therefore left it's unchanged.
```

**Windows Update Services**
```
The following update services get deleted instead of solely being removed since, they tend to reenable themselves.

1. Windows Update Medic Service. - (WaaSMedicSvc)
2. Windows Update. - (wuauserv)
3. Update Orchestrator. - (UsoSvc)

```

 

