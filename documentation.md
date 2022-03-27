# TX-2 Documentation

The main categories of documentation are:

1. Documentation produced by the TX-2 project itself.  For example
   explanation of the planned design, reference information for
   maintenance and documentation intended for TX-2 programmers.
1. Papers published by people who wrote software on and for the TX-2;
   Ivan Sutherland's thesis, for example.
1. Proposals, progress reports, and other administrative documentation
   relating to the TX-2 project and Lincoln Lab.  This mostly does not
   contain information of directly technical use, but can help
   establish the timing of changes and the motivation for changes.
1. Retrospectives of the TX-2 project and programs such as Sketchpad.

## Documentation Highlights

The TX-2 Technical Manual is the key reference work on the workings of
the TX2, while the User Handbook is the first place to look for the
kind of information a programmer would need to know.

## TX-2 Project Documentation

Lincoln Laboratory Division 6 was responsible for the development of
the TX-2.  Their memos normally begin with the digit 6.

### Introductory and Overview Material

1. Papers presented at the February 1957 Western Joint Computer
   Conference  (Los Angeles, California) by members of the TX-2
   project.
   * This gives an overview of the system, though some details
   (e.g. some details of the instruction word and the main memory
   store) changed subsequently.
   * Available from [bitsavers.org](http://www.bitsavers.org/pdf/mit/tx-2/TX-2_Papers_WJCC_57.pdf).
   * Also available from the [Charles Babbage Institute Archives:
     Lincoln Labs [includes TX-2], Box: 22. Academic computing
     collection, CBI 61. Charles Babbage Institute
     Archives](https://archives.lib.umn.edu/repositories/3/archival_objects/19391).
   * These papers include:
	 * The Lincoln TX-2 Computer Development.  Wesley A. Clark.
     * A Functional Description of the Lincoln TX-2
       Computer. J. M. Frankovich and H. P. Peterson.
     * The Lincoln TX-2 Input-Output System.  James W. Forgie.
	 * Memory Units in the Lincoln TX-2.  Richard L. Best.
	 * TX-2 Circuitry.  Kenneth H. Olsen.
1. TX-2 Introductory Notes, A. Vanderburgh, 24 February 1959.
   * This document is particularly important because it contains a
     clear description of the operation of deferred addressing (on
     page 23).  I have not seen a full and clear description of this
     elsewhere.
   * From [TX-2 Materials, 1959-1960, Box: 8. United States government
     computing collection, CBI 63. Charles Babbage Institute
     Archives](https://archives.lib.umn.edu/repositories/3/archival_objects/545729).
1. Some Examples of TX-2 Programming, H. Philip Peterson, July 1958.  Also known as Memorandum 6M-5780.
   These appear to have been prepared before some significant parts of
   the design (such as the address of the A register) were changed.
   * [Available from
     bitsavers.org](http://www.bitsavers.org/pdf/mit/tx-2/6M-5780_Some_Examples_of_TX-2_Programming_Jul1958.pdf);    [This appears to be the same document](http://www.bitsavers.org/pdf/mit/tx-2/TX-2_ProgExamp.pdf).
   * Also available from UMN: [Lincoln Labs \[includes TX-2\], Box: 22.
	 Academic computing collection, CBI 61. Charles Babbage Institute
     Archives.](https://archives.lib.umn.edu/repositories/3/archival_objects/19391)
1. User Program Measurement in a Time-Shared Environment.  Alan
   G. Nemeth and Paul D. Rovner.
   [Communications of the ACM, October 1971, Volume 14 Number 10](https://dl.acm.org/doi/abs/10.1145/362759.362810).
	   * Describes the use of the sync system with the TX-2's
         APEX time-sharing system.  Includes some details of the
         implementation of the sync system.

### TX-2 Users Handbook

The handbook describes the system's instruction set, peripherals and
some operational procedures and details (e.g. console controls and
indicators).  It also describes the system assembler, includes a
listing of the customary set-up of the boot code in the A and B
plug boards.

1. TX-2 Users Handbook Chapter 3 - Operation Code, August 1963.
   * [via bitsavers](http://www.bitsavers.org/pdf/mit/tx-2/TX-2_UserHandbook_ch3.pdf)
1. TX-2 Users Handbook, Alexander Vanderburgh, July 1961 / October
   1961 / August 1963.
   * [via
     bitsavers](http://www.bitsavers.org/pdf/mit/tx-2/TX-2_UsersHandbook_Nov63.pdf)
   * [via
     archive.org](https://archive.org/details/tx-2-users-handbook-nov-63) (searchable)
   * This is a more-complete copy, but it still does not include the
     sections on the Magnetic Tape storage or the plotter.

### TX-2 Technical Manual

Also known as Lincoln Manual No. 44. This was a three-volume work; I
have not yet found a copy of Volume 1.  I believe one exists in the
Lincoln Lab archive.

1. TX-2 Technical Manual Volume 1 (presumably Chapters 1 to 7)
1. TX-2 Technical Manual Volume 2 (Chapters 8 to
   15)
   * [via
     bitsavers](http://www.bitsavers.org/pdf/mit/tx-2/TX-2_TechManVol2_Jun61.pdf)
   * [via
     archive.org](https://archive.org/details/tx-2-tech-man-vol-2-jun-61) (searchable)
1. TX-2 Technical Manual Volume 3 (Chapter
   16)
   * [via
     bitsavers](http://www.bitsavers.org/pdf/mit/tx-2/TX-2_TechManVol3_Jul61.pdf)
   * [via
     archive.org](https://archive.org/details/tx-2-tech-man-vol-3-jul-61)
     (this version is searchable)

### APEX

APEX was introduced in 1964 and was a system for time-sharing on the TX-2.

1. A Time- and Memory-Sharing Executive Program for Quick-Response
   On-Line Applications.  Fall Joint Computer Conference, 1965.  AFIPS
   Conference Proceedings, Volume 27 Part 1.

### TX-2 Hardware

1. [6M-5661, Toggle Switch Storage System
   TX-2](http://www.bitsavers.org/pdf/mit/tx-2/6M-5661_Toggle_Switch_Storage_System_TX-2_Apr1958.pdf),
   Leopold Neumann, April 21, 1958.
1. The New Skip-on-Index Instruction, J. M. Frankovitch, February 4th,
   1960.
   * Lincoln Labs [includes TX-2], Box: 7. Academic computing
     collection, CBI 61. Charles Babbage Institute
     Archives. https://archives.lib.umn.edu/repositories/3/archival_objects/19391
1. A Computer-Integrated Rapid-Access Magnetic Tape System with Fixed
   Address.
   IRE-ACM-AIEE '58 (Western): Proceedings of the
   Western Joint Computer Conference: Contrasts in Computers
   May 6-8, 1958, Pages 42–46
   * Available from [ACM Digital Library](https://dl.acm.org/doi/10.1145/1457769.1457783)
   * Available from [bitsavers](http://www.bitsavers.org/pdf/mit/tx-2/A_Computer-Integrated_Rapid_Access_Magnetic_Tape_System_with_Fixed_Address.pdf)
1. A Discussion of the Circuitry Used in the Lincoln TX-2
   Computer.
   Jonathan R. Fadiman.  Lincoln Laboratory Memo 6D-2631, 1 October,
   1958.
   * Available from [bitsavers](http://www.bitsavers.org/pdf/mit/tx-2/TX-2_Circuitry.pdf)

## Papers on TX-2 Software

### Sketchpad

1. [Sketchpad, A Man-Machine Graphical Communication
   System](http://www.bitsavers.org/pdf/mit/tx-2/Sketchpad_A_Man-Machine_Graphical_Communication_System_Jan63.pdf),
   Ph.D thesis of Ivan Edward Sutherland, January 7, 1963.
1. [Sketchpad: A Man-Machine Graphical Communication
   System](http://www.bitsavers.org/pdf/mit/tx-2/Sketchpad_TR296_Jan63.pdf),
   Lincoln Laboratory Technical Report 296, January 30, 1963.

### Papers Closely Related to Sketchpad

1. Graphical Communication and Control Languages.  L. G. Roberts.
   Lincoln Laboratory, M.I.T.
   * This describes a list processing system which it states is
     similar to but not identical to those used in Sketchpad and
     Sketchpad-III.
   * Available from [researchgate.net](https://www.researchgate.net/profile/Lawrence-Roberts-2/publication/239592229_Graphical_communication_and_control_languages/links/589f54ac45851598bab71413/Graphical-communication-and-control-languages.pdf)

### Other TX-2 Software

1. [BCPL Reference
   Manual](http://www.bitsavers.org/pdf/mit/tx-2/TX-2_BCPL_Reference_Manual_May69.pdf),
   Martin Richards (M.I.T. Project MAC), Henry Ancona (Lincoln
   Laboratory), 6 May 1969.
1. [LO - A Text Formatting Program](https://apps.dtic.mil/sti/pdfs/ADA007824.pdf)
   A. Evans Jr, Lincoln Laboratory, 21 February 1975.

### Bill Sutherland's Thesis

1. The On-Line Graphical Specification of Computer Procedures.
   William Robert Sutherland, January, 1966.
   * [available from MIT libraries](https://mit.primo.exlibrisgroup.com/discovery/fulldisplay?vid=01MIT_INST:MIT&search_scope=all&tab=all&docid=alma990002681740106761&lang=en&context=L&virtualBrowse=true)
1. On-Line Graphical Specification of Computer Procedures.
   W. R. Sutherland, 23 May 1966, Lincoln Laboratory Technical
   Report 405.

## Administrative Documents

The quarterly status reports of several of the divisions of Lincoln
Laboratory (e.g. 2, 5, 6) provide some useful background information
about the stages in the build of the TX-2 computer.

### Division 2

1. [Division 2 Quarterly Progress Report: Data Systems, 15
   August 1964.](https://apps.dtic.mil/sti/pdfs/AD0604590.pdf)

## Retrospectives, Oral History, etc.

1. [An Interview with Ivan
   Sutherland](https://conservancy.umn.edu/bitstream/handle/11299/107642/oh171lis.pdf?sequence=1&isAllowed=y),
   OH 171, Conducted by William Aspray, 1 May 1989.  Charles Babbage Institute.
1. [Graphics in Time-Sharing: A Summary of the TX-2
   Experience](https://dl.acm.org/doi/10.1145/1476793.1476900)
   William R. Sutherland, James W. Forgie, Marie V. Morello.
1. [Interaction at Lincoln laboratory in the 1960's: looking forward
   -- looking back](https://doi.org/10.1145/1056808.1056864)
   William Buxton, Ron Baecker, Wesley Clark, Fontaine Richardson,
   Ivan Sutherland.
   CHI EA '05: CHI '05 Extended Abstracts on Human Factors in
   Computing Systems.  April 2005, Pages 1162–1167.
