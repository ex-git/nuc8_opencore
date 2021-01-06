# Unlock CFG

UEFITool: https://github.com/LongSoft/UEFITool/releases

ifrextract: https://github.com/LongSoft/Universal-IFR-Extractor/releases

modGRUBShell.efi: https://github.com/datasone/grub-mod-setup_var/releases


1. UEFITool search "CFG lock" text

2. Locate section

3. Extract body ===> Section_PE32_image_Setup_Setup_body.efi

4. convert to txt ===> ./ifrextract Section_PE32_image_Setup_Setup_body.efi cfg.txt

5. open cfg.txt search CFG lock found CFG lock address 0x6EF address value 0x1 is enabled. Need to change it to 0x0 to disable CFG lock.

6. modGRUBShell.efi rename to BOOTX64.efi put in EFI/BOOT, or put it in Tool and execute it with OpenShell

7. boot, grub shell ==> setup_var_3 0x6EF 0x0

8. reboot and verify lock status

```
Alternative method: use ru.efi 
Downloaded link and zip file password from website: http://ruexe.blogspot.com/
```

CFG Lock and Overclocking Lock from BIOS version: 0039
```
0x39D07 	Form: View/Configure CPU Lock Options, FormId: 0x273D {01 86 3D 27 C5 01}
0x39D0D 		One Of: CFG Lock, VarStoreInfo (VarOffset/VarName): 0x6EF, VarStore: 0x1, QuestionId: 0x22D, Size: 1, Min: 0x0, Max 0x1, Step: 0x0 {05 91 BE 03 BF 03 2D 02 01 00 EF 06 10 10 00 01 00}
0x39D1E 			One Of Option: Disabled, Value (8 bit): 0x0 {09 07 04 00 00 00 00}
0x39D25 			One Of Option: Enabled, Value (8 bit): 0x1 (default) {09 07 03 00 30 00 01}
0x39D2C 		End One Of {29 02}
0x39D2E 		One Of: Overclocking Lock, VarStoreInfo (VarOffset/VarName): 0x78B, VarStore: 0x1, QuestionId: 0x22E, Size: 1, Min: 0x0, Max 0x1, Step: 0x0 {05 91 BA 03 BB 03 2E 02 01 00 8B 07 10 10 00 01 00}
0x39D3F 			One Of Option: Disabled, Value (8 bit): 0x0 {09 07 04 00 00 00 00}
0x39D46 			One Of Option: Enabled, Value (8 bit): 0x1 (default) {09 07 03 00 30 00 01}
0x39D4D 		End One Of {29 02}
0x39D4F 	End Form {29 02}
```
