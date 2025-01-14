- DLLs
- You see them everywhere in windows
- ["a library that contains code and data that can be used by more than one program at the same time."](https://learn.microsoft.com/en-us/troubleshoot/windows-client/setup-upgrade-and-drivers/dynamic-link-library)
	- "For the Windows operating systems, much of the functionality of the operating system is provided by DLL."
	- "The use of DLLs helps promote modularization of code, code reuse, efficient memory usage, and reduced disk space. So, the operating system and the programs load faster, run faster, and take less disk space on the computer."
- When a DLL is loaded by a program, the DLL is assigned as a dependency.
	- This is exploitable by referencing a different, malicious DLL
- Loaded one of two ways:
	- Load-time dynamic linking
		- calls made from the application
		- requires a header and import library file
	- Run-time dynamic linking
		- a function inside of the process
			- `LoadLibrary`
			- `LoadLibraryEx`
		- after you load it, you have to identify it
		- malware typically uses this type of loading
			- may need to transfer files between memory, and one DLL is more manageable than headers or libraries