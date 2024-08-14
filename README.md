# Notes-From-Book-Driver-Dev
# Beginning a Driver Project
## History
- Early PCs used Intel processors in "real mode" with 640 KB of memory and manual hardware configuration through DIP switches.
- Windows evolved from a graphical shell for MS-DOS to a full operating system with virtual device drivers (VxDs) for multitasking and hardware virtualization.
- Microsoft developed the Windows Driver Model (WDM) to unify driver development across different Windows versions, eliminating the need for real-mode drivers by the time of Windows 98/Me.

## An Overview of the Operating Systems
The Windows Driver Model (WDM) unifies device driver development for the two parallel operating system lines: Windows 98/Me and Windows 2000/XP, despite their internal differences.
![image](https://github.com/user-attachments/assets/743a18b9-ccc2-42c0-97e3-48f05c4a19d0)

- Windows XP operates in two modes: user mode and kernel mode, with device interactions managed through APIs like ReadFile.
- The I/O Manager handles device interaction requests, converting them into I/O request packets (IRPs) for device drivers.
- NtReadFile, a kernel-mode routine, validates parameters, creates an IRP, and allows the device driver to process requests independently of the user-mode application.
