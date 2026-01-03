# Service Destroyer Changelog

**Service Destroyer V1.0**

8/22/25 <3

*What it did?*
- Disables Windows Services.
- Creates a backup of Services via the registry.

*Lite Version*
- Sets all Windows Services to Manual.
- Creates a backup of Services via the registry.

---

**Service Destroyer V1.1**

8/23/25 <3

*Added?*
- Added Split SVC code.

*Lite Version*
- Added Split SVC code.

---

**Service Destroyer V1.2**

8/24/25 <3

*Added?*
- Added ADPSvc Service.
- Added hpatchmon Service.
- Added whesvc Service.

*Fixed*
- Fixed "Blank login/Unable to log in" on non-offline accounts.
- Fixed "PIN unavailable issue" on non-offline accounts.

*Removed*
- Removed "NgcSvc" to fix no login.
- Removed "NgcCtnrSvc" to fix no login.
- Removed "KeyIso" to fix PIN unavailable issue.

*Lite Version*
- Same things done.

---

**Service Destroyer V1.3**

8/29/25 <3

*Fixed*
- Fixed LocalKdc "The specified service does not exist as an installed service." on older win 11 verions by nulling it.
- Fixed EventSystem and made it demand to prevent/force others to reenable it.         

*Added*
- Added CloudBackupRestoreSvc to sc config.
- Added NPSMSvc to sc config
- Added BcastDVRUserService to sc config.
- Added CaptureService to sc config.
- Added cbdhsvc to sc config.
- Added CDPUserSvc to sc config.
- Added ConsentUxUserSvc to sc config.
- Added DevicePickerUserSvc to sc config.
- Added DevicesFlowUserSvc to sc config.
- Added MessagingService to sc config.
- Added OneSyncSvc to sc config.
- Added P9RdrService to sc config.
- Added PenService to sc config.
- Added PimIndexMaintenanceSvc to sc config.
- Added UserDataSvc to sc config.
- Added UnistoreSvc to sc config.
- Added webthreatdefusersvc to sc config.
- Added WpnUserService to sc config.

*Redid*
- Redid the deletion of wuauserv, and made it disable instead.
- Redid the deletion of WaaSMedicSvc, and made it disable instead.
- Redid the deletion of UsoSvc, and made it disable instead.

*Removed*
- Removed Appinfo, since other would reenable UAC causing the this [Problem](https://github.com/QuakedK/Service-Destroyer/issues/2).
- Removed Disable UAC code since Appinfo is no longer disabled.

*Lite Version*
- Did nearly all the same changes but for manual/demand not disabled.
- Made Eventlog auto to fix this [Problem](https://github.com/QuakedK/Service-Destroyer/issues/3).

---

**Service Destroyer V1.4**

1/2/25 <3

*Removed*
- Removed "Spliting svchost.exe processes, based on RAM capacity in KB" code.
- Removed the deletion of CryptSvc. (Appears to cause, issues with certain Anti-Cheats)

*Added*
- Added new Split SvcHost code that uses the maximum possible DWORD value, instead of splitting it based on RAM capacity.

*Lite Version*
- Did nearly all the same changes, that were applicable for that version.
- Made WlanSVC auto to fix this wifi connection issues.
