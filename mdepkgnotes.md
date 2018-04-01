# [UDK2018]( https://github.com/tianocore/tianocore.github.io/wiki/UDK2018) MdePkg  Notes

1. [New Features and Changes](#new-features-and-changes)
2. [Bug Fixes](#bug-fixes)
3. [Known Issues](#known-issues)


##                                               NEW FEATURES AND CHANGES
1.  Add Unified Extensible Firmware(UEFI) specification 2.7 defined Protocols/PPIs/GUIDs and their related data     structure definitions.
     1)  Protocols:
        EFI_HII_POPUP_PROTOCOL
        EFI_HTTP_BOOT_CALLBACK_PROTOCOL
        EFI_NVDIMM_LABEL_PROTOCOL
        EFI_PARTITION_INFO_PROTOCOL
        EFI_RESET_NOTIFICATION_PROTOCOL
        EFI_UFS_DEVICE_CONFIG_GUID
     2)  GUIDs:
        EFI_BTT_ABSTRACTION_GUID
        EFI_ADAPTER_INFO_MEDIA_TYPE_GUID
        EFI_KMS_FORMAT_GENERIC_DYNAMIC_GUID
     3)  Miscellaneous elements:
         a) Add DNS_DEVICE_PATH device path
         b) Add definition EFI_FIRMWARE_ERROR_TYPE_SOC_TYPE1/_TYPE2
         c) Update struct EFI_FIRMWARE_ERROR_DATA
         d) Update struct EFI_FTP4_COMMAND_TOKEN
         e) Add definition HTTP_STATUS_308_PERMANENT_REDIRECT
         f) Correct definition HTTP_STATUS_300_MULTIPLE_CHOICES
         g) Deprecate attribute EFI_VARIABLE_AUTHENTICATED_WRITE_ACCESS
         h) Update EFI_SERIAL_IO_PROTOCOL.SetAttributes() return status
         i) Add the comments to address security problems in the Pkcs7Verify Protocol
         j) Correct EFI_RESET_NOTIFICATION_PROTOCOL.UnregisterResetNotify

2.  Add Platform Initialization(PI) specification 1.5/1.6 defined Protocols/PPIs/GUIDs and their related data     structure definitions.
     1)  Protocols:
        EFI_DXE_MM_READY_TO_LOCK_PROTOCOL
        EFI_MM_ACCESS_PROTOCOL
        EFI_MM_BASE_PROTOCOL
        EFI_MM_COMMUNICATION_PROTOCOL
        EFI_MM_CONFIGURATION_PROTOCOL
        EFI_MM_CONTROL_PROTOCOL
        EFI_MM_CPU_PROTOCOL
        EFI_MM_CPU_IO_PROTOCOL
        EFI_MM_END_OF_DXE_PROTOCOL
        EFI_MM_GPI_DISPATCH_PROTOCOL
        EFI_MM_IO_TRAP_DISPATCH_PROTOCOL
        EFI_MM_PCI_ROOT_BRIDGE_IO_PROTOCOL
        EFI_MM_PERIODIC_TIMER_DISPATCH_PROTOCOL
        EFI_MM_POWER_BUTTON_DISPATCH_PROTOCOL
        EFI_MM_READY_TO_LOCK_PROTOCOL
        EFI_MM_RSC_HANDLER_PROTOCOL
        EFI_MM_STANDBY_BUTTON_DISPATCH_PROTOCOL
        EFI_MM_STATUS_CODE_PROTOCOL
        EFI_MM_SW_DISPATCH_PROTOCOL
        EFI_MM_SX_DISPATCH_PROTOCOL
        EFI_MM_USB_DISPATCH_PROTOCOL
        EFI_LEGACY_SPI_CONTROLLER_GUID
        EFI_LEGACY_SPI_FLASH_PROTOCOL
        EFI_LEGACY_SPI_SMM_CONTROLLER_PROTOCOL
        EFI_LEGACY_SPI_SMM_FLASH_PROTOCOL
        EFI_SPI_CONFIGURATION_GUID
        EFI_SPI_HOST_GUID
        EFI_SPI_IO_PROTOCOL
        EFI_SPI_NOR_FLASH_PROTOCOL
        EFI_SPI_SMM_CONFIGURATION_PROTOCOL
        EFI_SPI_SMM_HC_PROTOCOL
        EFI_SPI_SMM_NOR_FLASH_PROTOCOL
     2)  Ppis:
        EFI_SEC_HOB_DATA_PPI
     3)  GUIDs:
        EFI_DISK_INFO_SD_MMC_INTERFACE_GUID
     4)  Miscellaneous elements:
         a) Correct EfiGcdMemoryTypePersistent name
         b) Add FFS_ATTRIB_DATA_ALIGNMENT_2
         c) Add EFI_FIRMWARE_VOLUME_EXT_ENTRY_USED_SIZE_TYPE
         d) Add EFI_HOB_FIRMWARE_VOLUME3
         e) Add EFI_MM_SYSTEM_TABLE
         f) Add EFI_PEI_FREE_PAGES
         g) Add EFI_SW_DXE_BS_PC_ATTEMPT_BOOT_ORDER_EVENT
         h) Deprecate SMM Communication ACPI Table
         i) Update description for notification PPI from SEC
         j) Correct the comments of EFI_PEI_RESET2_SYSTEM

3.  Add/Upgrade Industry standard definitions.
     1)  Add ACPI6.2 tables
     2)  Update ACPI6.0/ACPI6.1 tables
         a) Add missing PCCT subspace type 1 and 2 definitions
     3)  Add EFI_ACPI_DMAR_FLAGS_DMA_CTRL_PLATFORM_OPT_IN_FLAG
     4)  Add ACPI IO Remapping Table (IORT) definition
     5)  Add PCI vendor-specific capability header
     6)  Correct PCI_REG_PCIE_SLOT_CONTROL definition
     7)  Add new TPM bit for cancel currently executing command
     8)  Add NVME shutdown notification related macros 

4.  Add new Library classes.
     1)  PciSegmentInfoLib
     2)  S3PciSegmentLib

5.  Add new library APIs in existing library classes.
     1)  Add IsNodeInList(), CalculateCrc32(), AsmWriteTr() in BaseLib.
     2)  Add BuildFv3Hob() in HobLib
     3)  Add PeiServicesFreePages() and PeiServicesResetSystem2() in PeiServicesLib
     4)  Add DevPathFromTextDns() and DevPathToTextDns() in DevicePathLib

6.  Add new library instances.
     1)  BasePciSegmentInfoLibNull
     2)  BasePciSegmentLibSegmentInfo
     3)  DxeRuntimePciSegmentLibSegmentInfo
     4)  BaseS3PciSegmentLib
     5)  BaseIoLibIntrinsicSev

7.  Update Base definition
     1)  Add struct IA32_TASK_STATE_SEGMENT and IA32_TSS_DESCRIPTOR in BaseLib.h
     2)  Add two macro IA32_GDT_TYPE_TSS and IA32_GDT_ALIGNMENT in BaseLib.h
     3)  Correct and clarify documentation of VA_LIST in Base.h

8.  Disable the C4701 and C4703 warnings for VS2017

##                                                      BUG FIXES
1.  Update UefiDevicePathLib
     a) Fix byte orders of iSCSI.Lun in DevicePathFromText.
     b) Fix bug when converting iSCSI node that default TCP(0) should be used.

2.  Support more module types in UefiRuntimeLib.

3.  Update BaseLib
     a) Fix potential out-of-bound memory access in SafeString
     b) Avoid reading content beyond string boundary
     c) Update internal LinkedList verifications.

4.  Update BasePrintLib
     a) Fix possible negative value left shift

5.  Add macro PCI_ECAM_ADDRESS in IndustryStandard\PciExpress21.h

6.  Fix Xcode 9 Beta treating 32-bit left shift as undefined in BaseUefiDecompressLib

7.  Fix memory leak issue in DxeHstiLib

8.  Declare _ReturnAddress() in Base.h for MSFT tool chain


##   KNOWN ISSUES
1.  EFI_SIZE_TO_PAGES() macro requires that the input parameter is UINTN data type.

2.  SecPeiDxeTimerLibCpu library instance can be used by drivers of type DXE_RUNTIME_DRIVER and DXE_SMM_DRIVER in     their initialization without any issues. But, those driver needs be careful in the implementation     of runtime services and SMI handlers.

3.  BaseExtractGuidedSectionLib library instance can be used by drivers of type DXE_RUNTIME_DRIVER and DXE_SMM_DRIVER in     their initialization without any issues.
