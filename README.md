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

What Kind of Driver Do I Need? 
## ![image](https://github.com/user-attachments/assets/fd5ad58e-a694-43d8-a862-b7e515a58f37)


## The Two Basic Data Structures 
A WDM driver manages two key data structures: the driver object, which holds pointers to driver routines, and the device object, which represents and manages an instance of hardware.
### Driver Objects 
The I/O Manager uses the DRIVER_OBJECT data structure to represent each device driver. It includes both accessible and opaque fields (similar to public and private members in C++). The DRIVER_OBJECT is declared in the DDK headers, along with its pointer type and associated atomic data types, such as CSHORT for short integers. This declaration pattern is common in kernel-mode programming within the DDK.

### Device Objects 
A device object in a WDM driver includes fields like DriverObject, which references the associated driver, and NextDevice, which links to other device objects from the same driver, although the latter is rarely used by drivers due to synchronization complexities.
