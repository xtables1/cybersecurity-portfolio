1. Summary
This lab focuses on the behavior of spyware within a controlled environment. By utilizing the Any.Run interactive sandbox,
I executed a suspicious file (write.exe) to monitor its impact on a Windows 10 host. The goal was to identify Indicators of Compromise (IOCs),
including malicious process spawning, registry modifications, and suspicious network activity.

2. Environment & Tools
	• Sandbox: Any.Run (Interactive Analysis)
	• Operating System: Windows 10 (64-bit)
	• Analysis Type: Dynamic (Behavioral) Analysis
	• Target File: write.exe
	
3. Analysis Walkthrough

Phase 1: Sandbox Configuration
I configured the analysis environment to mimic a standard workstation. The target file, masquerading as a legitimate executable, was uploaded to the Any.Run portal.
	[Insert Screenshot 1: Any.Run dashboard showing the file upload and OS selection]
	
	
Phase 2: Execution and Monitoring
Upon execution, the process tree was monitored in real-time. Dynamic analysis revealed that write.exe initiated several sub-processes that are non-standard for
a basic text-editing utility.


Phase 3: Behavioral Observations
	• Process Spawning: The malware attempted to inject code into legitimate system processes.
	• Persistence: Observed attempts to modify registry keys to ensure the malware remains active after a system reboot.
	• Network Activity: The sandbox flagged outgoing traffic to suspicious IP addresses, likely attempting to reach a Command & Control (C2) server.
	[Insert Screenshot 2: The process graph or "HTTP/Stream" view from the Any.Run results]
	
	
4. Indicators of Compromise (IOCs)

During the investigation, the following artifacts were identified:

Artifact Type	Value / Description
Filename:	write.exe
Primary Action:	Credential harvesting and system monitoring
Registry Impact:	HKCU\Software\Microsoft\Windows\CurrentVersion\Run
Severity Level:	High (Malicious Activity Detected)
