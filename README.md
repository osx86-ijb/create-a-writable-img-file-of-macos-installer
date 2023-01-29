 <h1 align="center">Steps one would take to create a bootable .img file of a full macOS installer from within macOS, to be written to a USB device by users via any OS of their choosing.</h1>

```
1) Create blank disc image via disk utility (choose the read/write dmg choice)
2) Make it the same size as reported by createinstallmedia (safe bet would be 16GB)
3) Mount the dmg file
4) Use createinstallmedia against the mounted volume
5) Once it's created/finished, find the disk assignment for the mounted dmg
6) Use "sudo diskutil unmount Disk diskassignmentgoeshere" (don't use quotations when issuing command)
7) Once unmounted, use "dd if=/diskassignmentofdmggoeshere of=/whereeveryouwanttodumptheoutputimage.img bs=4096 conv=sync,noerror" (don't use quotations when issuing command)
8) After .img file has been created, write the file to USB device of choosing.
9) Mount the EFI/ESP partition of newly created USB device of macOS installer, and setup OpenCore / Clover bootloader on the EFI/ESP as normal.
10) After setting up the EFI/ESP specific to your hardware as required, boot from USB and proceed with macOS installation as normal.
```
