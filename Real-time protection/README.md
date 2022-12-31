# Useful commands
https://learn.microsoft.com/en-us/microsoft-365/security/defender-endpoint/linux-resources?view=o365-worldwide#supported-commands


# Set exclusion for scanning

1. To make exclusion on the files from the scanning of defender for endpoint solution

For windows machines, we can refer to the doc [Configure and validate exclusions based on extension, name, or location | Microsoft Learn](https://learn.microsoft.com/en-us/microsoft-365/security/defender-endpoint/configure-extension-file-exclusions-microsoft-defender-antivirus?view=o365-worldwide)

For Linux machines, we can refer to the doc https://learn.microsoft.com/en-us/microsoft-365/security/defender-endpoint/linux-exclusions?view=o365-worldwide

2. It is necessary to set up the exclusion for the process/app and the files it touched simultaneously.

>We can refer to the document [: Configure and validate exclusions for Microsoft Defender for Endpoint on Linux | Microsoft Learn](https://learn.microsoft.com/en-us/microsoft-365/security/defender-endpoint/linux-exclusions?view=o365-worldwide) to configure the exclusions that apply to on-demand scans, and real-time protection and monitoring.

>The supported exclusion types are as below and if we exclude a process, it will exclude the process and all files opened by it.

![image](https://user-images.githubusercontent.com/96930989/210125431-f5814095-aec5-41ef-8d59-7e7fc29ea607.png)


# FAQ
 
1. Whether the performance of VM would be affected once we enabled real-time protection in MDATP.

>Real-time protection (RTP) is a feature of Defender for Endpoint on Linux that continuously monitors and protects your device against threats. It consists of file and process monitoring and other heuristics.
	
>Performance problems are mainly caused by bottlenecks in one or more hardware subsystems, depending on the profile of resource utilization on the system. Sometimes applications are sensitive to disk I/O resources and may need more CPU capacity, and sometimes some configurations are not sustainable, and may trigger too many new processes, and open too many file descriptors.
	
>Depending on the applications that you are running and your device characteristics, you may experience suboptimal performance when running Defender for Endpoint on Linux. In particular, applications or system processes that access many resources such as CPU, Disk, and Memory over a short timespan can lead to performance issues in Defender for Endpoint on Linux.
	
>We recommend choosing a small set of non-production VMs to enable real-time protection and monitor the performance first. After validation, feedback, and configuring the suitable exclusions to address the performance issue if any, we start the gradual rollout process to the rest of the VMs.
	
 2. Where to find the table to view all the process running at present so as to decide if we need to configure exclusion for specified process.
	
>We can follow the steps in the document: [Troubleshoot performance issues for Microsoft Defender for Endpoint on Linux | Microsoft Learn](https://learn.microsoft.com/en-us/microsoft-365/security/defender-endpoint/linux-support-perf?view=o365-worldwide#troubleshoot-performance-issues-using-real-time-protection-statistics)

>The tool will provide us the real-time statistics for your reference as below sample:
	![image](https://user-images.githubusercontent.com/96930989/210125263-1c8cc644-7294-4886-b296-d432856cd81b.png)
