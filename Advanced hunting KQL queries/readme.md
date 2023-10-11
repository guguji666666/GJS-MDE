## Advanced hunting KQL queries
```kusto
DeviceTvmSoftwareVulnerabilitiesKB
| join kind= inner ( 
DeviceTvmSoftwareVulnerabilities
| where VulnerabilitySeverityLevel in ("High", "Critical")
) on CveId 
| join kind= inner ( 
DeviceInfo  
) on DeviceId
| where DeviceName contains "<your device name>"
| project DeviceId, DeviceName, CveId, IsExploitAvailable, VulnerabilitySeverityLevel, VulnerabilityDescription, OSPlatform, OSVersion, Timestamp, ReportId
```
