# Qoi2Spr

Qoi2Spr is a suite of applications for converting images in the [QOI (Quite OK Image) format](https://qoiformat.org/) to RISC OS Sprite, and vice versa.

It is available as:

* A Wimp application, !Qoi2Spr, which also runs in a TaskWindow, to convert QOI files to Sprites.

* A TransLoader, !TransQOI, which enables applications which use Computer Concepts' FFG protocol, such as OvationPro and PrivateEye, to load QOI files as Sprites.

* A PhotoDesk converter, !3QOI, which enables PhotoDesk to load and save QOI files.

* An ImageFileConverter module, ConvertQOI, for RISC OS 4 and 6.


# Installation

The minimum RISC OS version supported is 3.50. However, the Wimp application and TransLoader can be made to run on RISC OS 3.10 with some modifications, detailed below.

Installation instructions are below. Each programme has it's own help file with further information.

To set the filetype of a QOI file downloaded from the Internet or from a Windows PC, add the following to your Mimemap file:
```
    image/x-qoi		QOI		a61	.qoi
```


## Wimp application

Copy the application "!Qoi2Spr" into a suitable directory.


## TransLoader

Copy the application "TransLoader.!TransQOI" into a suitable directory such as !OvnPro.AutoRun


## PhotoDesk

Copy the application "PhotoDesk.!3QOI" into !Photodesk.Resources.Formats


## RISC OS 4 ImageFileConverter

Copy the "RISCOS4.ConvertQOI" directory into !Boot.Choices.Users.Single.Boot.PreDesk, or wherever is appropriate for your setup.


# RISC OS 3.10

The Wimp application "!Qoi2Spr" and the TransLoader "!TransQOI" can be made to run on RISC OS 3.10 with the following modifications:
1. In !Run, remove the 3.50 check that starts: `RMEnsure UtilityModule 3.50`
2. Remove the files: `!Sprites11` and `!Sprites22`
3. In !Qoi2Spr.!RunImage, and/or !TransQOI.!Convert, in PROCheap_create replace:
```
       SYS "OS_ReadDynamicArea",-1 TO ,,HEAP_MAXSIZE%
```
   with:
```
       HEAP_MAXSIZE% = 28*1024*1024 : REM Max Wimpslot size = 28Mb
```

!Paint does not know about Type 6 (32bpp) Sprites and so you will not be able toview or edit the Sprites created in it, but !ChangeFSI is able to convert them into a suitable Sprite format for !Paint to load, although you do then lose any mask, but you can then add the mask back.


# History

1.00 : Initial release

