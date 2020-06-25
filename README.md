Patch Editor/Librarian the XFM2 FM synth

Beta 1 release June 12 2020


This is an editor/librarian for the XFM2 FPGA synthesizer designed by Rene Ceballos. Details of the 
design and instructions for building the XFM2 are at Rene's website: https://www.futur3soundz.com/


Other useful XFM2 resources: https://github.com/xerhard/XFM2-resources


Video demonstration of the XFM2 and the patch editor: https://www.youtube.com/watch?v=Ny7eByV2aGQ


The XFM2 editor was created using CTRLR https://ctrlr.org/

Many thanks to the authors of the DX7 and TG33 CTRLR panels - I learned a lot from their work and used quite a bit of their graphics and code. 
I could not have achieved this without their efforts to guide me. I was still a helluva lot of work!

You will need to install CTRLR to use this editor a.k.a. a CTRLR panel. I recommend version
5.3.201 which is the current stable release. I had lots of issues with later releases of CTRLR.

The editor uses MIDI sysex messages only and does not use the XFM2 USB connection - but you will still need USB to power the XFM2.
You will need a MIDI adapter for your computer and you will have to build the XFM2 with MIDI in and MIDI out connectors.

The panel should be self explanatory if you have read Rene's documentation but managing patches 
deserves some explanation. The "Patch" subpanel on the global controls tab is where you load and save patches. 
There are four memories we have to manage:


Working (RAM) memory on the XFM2

Patch storage memory on the XFM2

Editor memory (state of the UI controls)

Disk storage


The "PGM Select" button sends MIDI program change messages to the XFM2 - this causes the XFM2 to load that program from patch storage to working memory.

To sync the editor UI to the XFM2 use "load"/"program from XFM2". After this is done any changes to the UI controls will be sent to the XFM2 and they should both stay in sync.

To save the current state of the XFM2 RAM to patch storage memory, first set the write slot (patch number) you want to use and "save"/"program to XFM2".

To save the current state of the editor to disk use "save"/"program to file"

To load a patch from disk use "load"/"program from file". This will load the editor AND the XFM2 RAM with the patch.


I wrote a utility "dx72xfm2" which converts DX7 patch banks (32 patches) to sysex files that can be loaded by the XFM2.
The converter is not perfect but most patches should be pretty close to the DX7 sounds. You will probably want to tweek them with the editor anyway!

https://github.com/rheslip/dx72xfm2


Format of the .syx files:

5 byte header 0xf0 0x43 0x00 0x00 0x00   - 3rd byte is XFM2 unit number, always 0 in .syx files

512 parameters stored in MSB LSB midi format. range of most XFM2 parameters is 0-255

1 byte trailer 0xf7




Rich Heslip rheslip@hotmail.com

