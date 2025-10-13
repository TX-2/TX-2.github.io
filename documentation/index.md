# TX-2 Documentation

## Contents

* TOC
{:toc}

## Overview

The main categories of documentation are:

1. A [description of the TX-2](commentary/tx2.md) for modern readers.
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
1. Project documentation, including [commentary](commentary) on the
   primary sources.

There are also some related [photographs](photographs.md) and [videos](videos).

## How You Can Help

If you know of additional material that's not listed here, please let
us know (for example by email to james@youngman.org).  Even if you
can't give it to us directly (e.g. because Lincoln Lab would need to
release it), it will be useful for us to know that it exists.

## Documentation Highlights

The [TX-2 Technical Manual](#TM) is the key reference work on the
workings of the TX2, while the [User Handbook](#UH) is the first place
to look for the kind of information a programmer would need to know.

## Lincoln Laboratory TX-2 Project Documentation

Lincoln Laboratory Division 6 was responsible for the development of
the TX-2.  Their memos normally begin with the digit 6.

### Introductory and Overview Material

1. Papers presented at the February 1957 Western Joint Computer
   Conference  (Los Angeles, California) by members of the TX-2
   project.
   * This gives an overview of the system, though some details
   (e.g. some details of the instruction word and the main memory
   store) changed subsequently.
   * These papers are collected in a Lincoln Lab memo, 6M-4968.
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
   G. Nemeth and Paul D. Rovner.  [Communications of the ACM, October
   1971, Volume 14 Number
   10](https://dl.acm.org/doi/abs/10.1145/362759.362810); this
   describes the use of the sync system with the TX-2's APEX
   time-sharing system.  Includes some details of the implementation
   of the sync system.

### TX-2 Users Handbook {#UH}

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
   * [also via archive.org, but is a copy of the bitsavers document](https://archive.org/details/bitsavers_mittx2TX2U_9517142)
   * This is a more-complete copy, but it still does not include the
     sections on the Magnetic Tape storage or the plotter.

### TX-2 Technical Manual {#TM}

Also known as Lincoln Manual No. 44. This was a three-volume work.

1. TX-2 Technical Manual Volume 1 (Chapters 1 to 7)
   * [via bitsavers](http://www.bitsavers.org/pdf/mit/tx-2/LM-44v1_TX-2_Technical_Manual_Volume_1_196105.pdf)
   * Bitsavers uploaded this to
     [archive.org](https://archive.org/details/bitsavers_mittx2LM44lVolume1196105_174243236)
   * James Youngman uploaded a scan provided by Lincoln Lab to [archive.org](https://archive.org/details/mit-tx2-lm-44-1961-06/LM-44v1_sm)
1. TX-2 Technical Manual Volume 2 (Chapters 8 to
   15)
   * [via
     bitsavers](http://www.bitsavers.org/pdf/mit/tx-2/LM-44v2_TX-2_Technical_Manual_Volume_2_196106.pdf) ([alternative copy via
     bitsavers](http://www.bitsavers.org/pdf/mit/tx-2/TX-2_TechManVol2_Jun61.pdf))
   * [via
     archive.org](https://archive.org/details/tx-2-tech-man-vol-2-jun-61)
     (searchable)
1. TX-2 Technical Manual Volume 3 (Chapter
   16)
   * [via bitsavers](http://www.bitsavers.org/pdf/mit/tx-2/LM-44v3_TX-2_Technical_Manual_Volume_3_196107.pdf) ([alternative copy via
     bitsavers](http://www.bitsavers.org/pdf/mit/tx-2/TX-2_TechManVol3_Jul61.pdf))
   * [via
     archive.org](https://archive.org/details/tx-2-tech-man-vol-3-jul-61)
     (this version is searchable)

The TX-2 Technical Manual is [also available as a combined document at
archive.org](https://archive.org/details/mit-tx2-lm-44-1961-06)

The chapters of the Technical Manual are

* Volume 1
   * Chapter 1: Introductory Description
   * Chapter 2: Functional Description of TX-2
   * Chapter 3: Circuit Logic Elements
   * Chapter 4: Memories
   * Chapter 5: Timing and Control
   * Chapter 6: Funcitonal Organization of the Control Element
   * Chapter 7: Operation Codes
* Volume 2
   * Chapter  8: Pulse and Level Notation
   * Chapter  9: Computer Dynamics
   * Chapter 10: Control Element
   * Chapter 11: Memory Element
   * Chapter 12: Program Element
   * Chapter 13: Exchange Element
   * Chapter 14: Arithmetic Element
   * Chapter 15: In-Out Element
* Volume 3
   * Chapter 16: Timing Charts

### Programming

The Users Handbook contains a lot of information useful to programming
for the TX-2.

1. The New Skip-on-Index Instruction, J. M. Frankovitch, February 4th,
   1960.
   * Lincoln Labs [includes TX-2], Box: 7. Academic computing
     collection, CBI 61. Charles Babbage Institute
     Archives. [https://archives.lib.umn.edu/repositories/3/archival_objects/19391](https://archives.lib.umn.edu/repositories/3/archival_objects/19391)

### APEX

APEX was introduced in 1964 and was a system for time-sharing on the
TX-2.

Sketchpad pre-dates APEX.  Sketchpad is our primary focus for the
simulator.  The BCPL compiler used APEX, but we don't have details of
APEX or a copy of the BCPL compiler.

1. A Time- and Memory-Sharing Executive Program for Quick-Response
   On-Line Applications, James W. Forgie. Fall Joint Computer
   Conference, 1965.
   [AFIPS Conference Proceedings, Volume 27 Part 1.](https://dl.acm.org/doi/pdf/10.1145/1463891.1463956)

### TX-2 Hardware

The [Technical Manual](#TM) and [Users Handbook](#UH) contain a lot of
useful information.  Also see the [Introductory and Overview
Material](#introductory-and-overview-material).

#### Peripherals

The [Users Handbook](#UH) contains a lot of information about the
TX-2's peripherals.

##### Magnetic Tape Storage

1. A Computer-Integrated Rapid-Access Magnetic Tape System with Fixed
   Address.
   IRE-ACM-AIEE '58 (Western): Proceedings of the
   Western Joint Computer Conference: Contrasts in Computers
   May 6-8, 1958, Pages 42–46
   * Available from [ACM Digital Library](https://dl.acm.org/doi/10.1145/1457769.1457783)
   * Available from
     [bitsavers](http://www.bitsavers.org/pdf/mit/tx-2/A_Computer-Integrated_Rapid_Access_Magnetic_Tape_System_with_Fixed_Address.pdf)

##### Lincoln Writer

1. [The Lincoln Keyboard - a typewriter keyboard designed for computers
   imput flexibility](https://doi.org/10.1145/368873.368879).  A. Vanderburgh.
   Communications of the ACM, Volume 1, Issue 7, July 1958.
1. [The Lincoln
   Writer](https://apps.dtic.mil/sti/trecms/pdf/AD0235247.pdf).
   J. T. Glmore, Jr., R. E. Sewell.  Lincoln Laboratory Group report
   51-8.  October 6, 1959. ([archive.org](https://archive.org/details/ad-0235247))
1. [Lincoln Lab Memo
   M-5001-11](https://archive.org/details/bitsavers_mittx0memoug59_92242/mode/2up)
   "New Flexowriter Type Face" of 1959-08-27, by J. B. Dennis
   describes a flexowriter with a TX-2 typeface for use with the TX-0.
   The memo compares the "standard" and Lincoln type faces.

#### Other

1. [A Discussion of the Circuitry Used in the Lincoln TX-2
   Computer](http://www.bitsavers.org/pdf/mit/tx-2/TX-2_Circuitry.pdf).
   Jonathan R. Fadiman.  Lincoln Laboratory Memo 6D-2631, 1
   October, 1958. Available from
   [bitsavers](http://www.bitsavers.org/pdf/mit/tx-2/TX-2_Circuitry.pdf).
1. [6M-5661, Toggle Switch Storage System
   TX-2](http://www.bitsavers.org/pdf/mit/tx-2/6M-5661_Toggle_Switch_Storage_System_TX-2_Apr1958.pdf),
   Leopold Neumann, April 21, 1958.


## Papers on TX-2 Software

See also the page on the [software](software) described by these papers.

### Sketchpad

1. [Sketchpad, A Man-Machine Graphical Communication
   System](http://www.bitsavers.org/pdf/mit/tx-2/Sketchpad_A_Man-Machine_Graphical_Communication_System_Jan63.pdf),
   Ph.D thesis of Ivan Edward Sutherland, January 7, 1963.
1. [Sketchpad: A Man-Machine Graphical Communication
   System](http://www.bitsavers.org/pdf/mit/tx-2/Sketchpad_TR296_Jan63.pdf),
   Lincoln Laboratory Technical Report 296, January 30, 1963.
1. [Sketchpad listings and memoranda pertaining to TX-2 computer and
   programming](https://www.computerhistory.org/collections/catalog/102726903).
   Computer History Museum; catalog number 102726903.
   * The listings come in two documents.  Large sections of these are
     illegible.  These listings appear to have been printed on the
     TX-2's Xerox printer and then photocopied.  Many of the key
     details of the listing are unrecognizable blobs.  TX-2 assembly
     language makes extensive use of superscripts and subscripts, and
     the small size of these has meant that the photocopying did not
     always come out well.
1. In [Specialized Computer Equipment for Generation and Display of
   Three Dimensional Curar
   Figures](https://archive.org/details/DTIC_AD0406608/page/n15/mode/2up),
   March 1963 (MIT Electronic Systems Laboratory report ESL-TM-167),
   Robert H. Stots states that Sutherland's estimates for his TX-2
   programs are that, "of the time they spend on generation of the
   display list about 10% is spent on orienting the window to the
   total picture, about 10% on deciding which parts of the picture are
   within the view of this window, and 80% on generating the point
   list."

See also [Sketchpad videos](videos#sketchpad).

### Sketchpad-III {#Sketchpad-III}

1. Sketchpad-III, Three-Dimensional Graphical Communication With A
   Computer,
   Ph.D thesis of Timothy Edward Johnson, May 1963.
1. Sketchpad III: a computer program for drawing in three dimensions.
   Timothy E. Johnson.
   [AFIPS '63 (Spring): Proceedings of the May 21-23, 1963, Spring
   Joint Computer Conference, May 1963. Pages
   347–353](https://doi.org/10.1145/1461551.1461592).

See also [Sketchpad-III videos](videos#sketchpad-iii).

## Other TX-2 Software

1. [BCPL Reference
   Manual](http://www.bitsavers.org/pdf/mit/tx-2/TX-2_BCPL_Reference_Manual_May69.pdf),
   Martin Richards (M.I.T. Project MAC), Henry Ancona (Lincoln
   Laboratory), 6 May 1969.
1. [LO - A Text Formatting Program](https://apps.dtic.mil/sti/pdfs/ADA007824.pdf)
   A. Evans Jr, Lincoln Laboratory, 21 February 1975.

## Work Done with the TX-2

### Human/Computer Interaction

1. The On-Line Graphical Specification of Computer Procedures.
   William Robert Sutherland, January, 1966.
   * [available from MIT libraries](https://mit.primo.exlibrisgroup.com/discovery/fulldisplay?vid=01MIT_INST:MIT&search_scope=all&tab=all&docid=alma990002681740106761&lang=en&context=L&virtualBrowse=true)
1. On-Line Graphical Specification of Computer Procedures.
   W. R. Sutherland, 23 May 1966, Lincoln Laboratory Technical
   Report 405.
1. Graphical Communication and Control Languages.  L. G. Roberts.
   Lincoln Laboratory, M.I.T.
   * This describes a list processing system which it states is
     similar to but not identical to those used in Sketchpad and
     Sketchpad-III.
   * Available from [researchgate.net](https://www.researchgate.net/profile/Lawrence-Roberts-2/publication/239592229_Graphical_communication_and_control_languages/links/589f54ac45851598bab71413/Graphical-communication-and-control-languages.pdf)
2. Graphical Manipulation Techniques using the Lincoln TX-2,
   H. H. Loomis Jr.

### Graphics

1. Machine Perception of Three-Dimensional Solids.  Lawrence Gilman
   Roberts, June 1963. [Available from MIT
   libraries](https://dspace.mit.edu/bitstream/handle/1721.1/11589/33959125-MIT.pdf?sequence=2&isAllowed=y)

Roberts' work used a "ring list" representation for drawings.  This is
similar to but not identical to the methods used in Sketchpad and
Sketchpad-III (see page 59 of Roberts' thesis).  We don't have a
listing of the program on which the thesis is based, and the thesis
does not include code.

### Image Processing

1. L. D. Earnest worked on [Machine Recognition of Recursive
   Writing](https://archive.org/details/MachineRecognitionOfCursiveWriting)
   (MITRE Corp.) (1962)
1. James E. Cunningham worked on Image Correction on the TX-2; see
   [page 244 of the Quarterly Report of MIT. Research Laboratory of
   Electronics For The Three month period ending 31 May
   1963](https://archive.org/details/DTIC_AD0414870/page/244/mode/1up)

### Networking {#Networking}

1. The ARPANET Completion Report, by F. Heart, A. McKenzie, J.
   McQuillian, and D. Walden, BBN Report 4799, January 4, 1978.
   Available from
   [walden-family.org](https://walden-family.com/bbn/arpanet-completion-report.pdf)
   and
   [archive.org](https://archive.org/details/arpanet-completion-report).

### Speech Recognition and Audio Processing

1. Gold, B., Pitch Extraction on the TX-2
   Computer. J. Acoust. Soc. Am., 33, 1664-1665 (A) (1961)
1. James W. Forgie and Carma D. Forgie worked on speech recognition
   using the TX-2; see [page 287 of Current Research and Development in
   Scientific Documentation No,
   11](https://archive.org/details/DTIC_AD0403518/page/287/mode/1up),
   1962-11-01.
   Edwin B. Newman states in "Paracomputers in Psychological
   Research", on page 241 of [Harvard Symposium on Digital Computers and
   Their Applications (1961 : Brookline,
   Mass.)](https://archive.org/details/proceedings0000harv/page/240/mode/2up)
   that these programs were initially written for the
   Whirlwind computer and were later adapted for the TX-2.

### Brain and Nerual Research

Wes Clark did more work in this field on other machines including the LINC.

1. [Activity in Networks of Neuron-Like Elements](https://archive.org/details/bitsavers_mittx2LM44lVolume1196105_174243236/mode/2up),
   R. G. Farley and W. A Clark.  Symposium on Information Theory,
   Royal Institution, London, 1960-08-29 to 1960-09-02 (Cilin Cherry, Ed.).

### Other Topics

1. [Aspects of Associative Processing](https://stacks.stanford.edu/file/druid:mg700by4509/mg700by4509.pdf), J. A. Feldman, MIT Lincoln
   Laboratory Group 23 Technnical Note 1965-13, 21 April 1965.


## Conferences

1. The 1957 Western Joint Computer Conference  (Los Angeles, California)
   included multiple presentations about the TX-2. These papers are
   available from
   [bitsavers.org](http://www.bitsavers.org/pdf/mit/tx-2/TX-2_Papers_WJCC_57.pdf). For
   the papers themselves see "[Introductory and Overview
   Material](#introductory-and-overview-material)" above.
1. The [1959 Eastern Joint Computer
   Conference](https://dl.acm.org/doi/proceedings/10.1145/1460299)
   featured a trip (1959-12-02) featuring an inspection and a
   demonstration of the TX-2 computer (from [Datamation,
   November-December 1959, page
   46](https://archive.org/details/sim_datamation_november-december-1959_5_6/page/46/mode/1up)).
   The trip was hosted by A. Vanderburgh (per the list of personnel in
   the [conference proceedings](https://dl.acm.org/action/showFmPdf?doi=10.1145%2F1460299)).
1. 1965 Fall Joint Computer Conference
   * A Time- and Memory-Sharing Executive Program for Quick-Response
   On-Line Applications


## News Coverage

### 1957
{:.no_toc}

1. [Computers and Automation, Volume 6 Issue 1 (January
   1957)](https://archive.org/details/sim_computers-and-people_1957-01_6_1/mode/2up):
   mentions the TX-2 related talks at the upcoming Western Joint
   Computer Conference, scheduled for the morning of Feb 28.
1. [Digital Computer Newsletter, Volume 9
   No. 2 (April 1957)](https://archive.org/details/bitsavers_onrDigitaligitalComputerNewsletterV09N02Apr57_1388449)
   (page 4): describes construction of the TX-2 and outlines its size,
   speed and multi-sequence operation, decribing it as a
   "general-purpose parallel binary machine".
1. [Computers and Automation, Volume 6 Issue 4 (April
   1957)](https://archive.org/details/sim_computers-and-people_1957-04_6_4)
   (page 28): briefly decribes the talks given at the Western Joint
   Computer Conference, Statler Hotel, Los Angeles, 1957-02-26 to
   1957-02-28.

### 1959
{:.no_toc}

1. [MIT Technology Review, March
   1959](https://archive.org/details/MIT-Technology-Review-1959-03/page/n25/mode/2up):
   briefly mentions the TX-2's multiplication speed and work on speech
   and pattern recognition, in a general article on the work of
   Lincoln Lab.
1. [Control Engineering, September
   1959](https://archive.org/details/sim_control-engineering_1959-09_6_9/page/166/mode/2up):
   Digital components by both Digital Equipment Corp. and Harvey-Well
   Electronics Inc. are both derived from work on computers at the
   Lincoln Laboratory.
1. [Datamation, Sptember-October 1959, Volume 5 Issue
   5](https://archive.org/details/sim_datamation_september-october-1959_5_5/mode/2up):
   Magnetic Film Memory In Operation at Lincoln.
1. [Computers and Automation, October 1959, Volume 8 Issue
   10](https://archive.org/details/sim_computers-and-people_1959-10_8_10/page/6/mode/2up):
   John A. Kessler, First successful operation of a Practical Magnetic
   Film Memory.
1. [Electronic Industries, October 1959, Voolume 18 Issue
   10](https://archive.org/details/sim_electronic-industries_1959-10_18_10/page/106/mode/2up):
   What's New ... Magnetic Film Memory
1. [Automatic Data Processing,October 1959, Volume 1 Issue
   9](https://archive.org/details/sim_automatic-data-processing_1959-10_1_9/page/44/mode/2up):
   High-Speed Magnetic Film Memory.
1. [MIT Technology Review, November
   1959](https://archive.org/details/MIT-Technology-Review-1959-11/page/n23/mode/2up):
   Magnetic-Film Computer Memory.
1. [The Computer Bulletin Index, Volume 3 (December
   1959)](https://archive.org/details/itnow_1959-1960_3/mode/2up):
   Mentions the TX-2's magnetic-film memory.

### 1960
{:.no_toc}

1. [Digital Computer Newsletter, Volume 12 No. 1 (Jan
   1960)](https://archive.org/details/bitsavers_onrDigitaligitalComputerNewsletterV12N01Jan60_2755110)
   (page 29): high-speed magnetic-film memory.

## Administrative Documents

The periodic status reports of several of the divisions of Lincoln
Laboratory (e.g. 2, 5, 6) provide some useful background information
about the stages in the build of the TX-2 computer.  See [Lincoln
Laboratory Progress Reports](ll-progress-reports).

## Retrospectives, Oral History, etc.

1. [An Interview with Ivan
   Sutherland](https://hdl.handle.net/11299/107642),
   OH 171, Conducted by William Aspray, 1 May 1989.  Charles Babbage Institute.
1. [The TX-2 Computer and
   Sketchpad](https://www.ll.mit.edu/sites/default/files/page/doc/2018-05/LookingBack_19_1.pdf),
   Lincoln Laboratory Journal, Volume 19, Number 1, 2012.
1. [Graphics in Time-Sharing: A Summary of the TX-2
   Experience](https://dl.acm.org/doi/10.1145/1476793.1476900)
   William R. Sutherland, James W. Forgie, Marie V. Morello.
1. [Interaction at Lincoln laboratory in the 1960's: looking forward
   -- looking back](https://doi.org/10.1145/1056808.1056864)
   William Buxton, Ron Baecker, Wesley Clark, Fontaine Richardson,
   Ivan Sutherland.
   CHI EA '05: CHI '05 Extended Abstracts on Human Factors in
   Computing Systems.  April 2005, Pages 1162–1167.
1. The LINC was Early and Small.  Wesley A. Clark.
   [HPW '86: Proceedings of the ACM Conference on The history of
   personal workstations. January 1986 Pages
   133–155](https://doi.org/10.1145/12178.12187). [Video](https://www.youtube.com/watch?v=l9YBZo30Ses&list=PLQsxaNhYv8dbIuONzZcrM0IM7sTPQFqgr).

## Changes to the TX-2

There are some discrepancies between the primary documents listed
above.  The primary cause of this appears to be the fact that the TX-2
computer was changed, both during the design and build process and
also while in regular operation (routine changes occurred on
Wednesdays).

Primary sources will likely reflect these changes.  Here are some
examples:

* [Sequence number assignments](commentary/sequence-changes.md)
* [Opcodes](commentary/opcode-changes.md)
* The Arithmetic Element register addresses were moved to accommodate
  [Plugboard B](commentary/plugboard-B.md).

### Plans to Shut the TX-2 Down
{:.no_toc}

* [DTIC_ADA008503](https://archive.org/details/DTIC_ADA008503) (mentions transfer away
  from TX-2)
* [DTIC_ADA016399](https://archive.org/details/DTIC_ADA016399) (mentions transfer away
  from TX-2)
* [DTIC_ADA012734](https://archive.org/details/DTIC_ADA012734) (mentions planned shutdown)


## Uncategorised

* [DTIC AD0655810](https://archive.org/details/DTIC_AD0655810) (LEAP
  and VITAL)
* [DTIC AD0691815](https://archive.org/details/DTIC_AD0691815)
  (Initial Experiments on the Effects of System Delay on On-Line
  Problem Solving)
* [DTIC AD0694055](https://archive.org/details/DTIC_AD0694055)
  (networking) (An Experimental Computer Network)
* [DTIC AD0713221](https://archive.org/details/DTIC_AD0713221) (The
  LEAP User's Manual)
* [DTIC AD0727768](https://archive.org/details/DTIC_AD0727768) (Development of a 10,000,000 Bit Magnetic Film Memory)
* [DTIC AD0773831](https://archive.org/details/DTIC_AD0773831) (An
  Interface to the ARPA Network for the CP/CMS Time-Sharing
  System. Volume 1) Mentions TX-2.
