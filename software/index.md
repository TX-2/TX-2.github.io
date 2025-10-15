# TX-2 Software

* TOC
{:toc}

The project currently has some listings of TX-2 software, but as yet
we have no known-correct source code and no known-correct binary.

The main problem is that we only have scans of code and it's difficult
to ensure that these are error-free.  See [Verifying
Listings](verifying-listings.md) for an explanation of how we plan to
do this.

With accurately transcribed authentic software, we can test the
simulator and demonstrate that it is a credible re-creation of the
TX-2 machine.

## Listings we Have Already

* [Some Examples of TX-2
  Programming](http://www.bitsavers.org/pdf/mit/tx-2/6M-5780_Some_Examples_of_TX-2_Programming_Jul1958.pdf),
  H. Philip Peterson, July 1958.
   * Some short programs demonstrating how the planned machine was
     intended to work.
* Listings in the [Users
  Handbook](documentation#tx-2-users-handbook) provide the boot
  code and the standard paper tape reader leader.
* Sketchpad
   * The Computer History museum holds a [listing of
  Sketchpad](https://www.computerhistory.org/collections/catalog/102726903).
   * The TX-2 project is working on a [transcription of the Sketchpad
  source code to a machine-readable format](https://github.com/TX-2/Sketchpad).
* A listing of the program from Leonard Kleinrock's thesis, [Message
  Delay in Communication Nets with
  Storage](https://www.lk.cs.ucla.edu/data/files/Message%20delay%20Phd.pdf).
  The [listing of Professor Kleinrock's
  program](https://www.computerhistory.org/collections/catalog/300000161/)
  is available at the Computer History Museum.
  This listing is in the form of a PDF file containing scans, and so
  it's not in a form we can feed to the assembler.  We have an
  in-progress [transcription of the source
  code](https://github.com/TX-2/Kleinrock-network-simulator).

## We Need Machine-Readable Code

Known-good machine-readable code would act as a reality-check for our
understanding of the TX-2.  This would allow us to complete the
simulator with come confidence about its correctness.

If we can be reasonably confident about the correctness of the
simulator, then it may become tractable to try to reconstruct the
illegible portions of the Sketchpad listing.  This of course would be
a huge task.

If we could obtain a machine-readable copy of the Sketchpad code, this
would allow us to make that program run again for the first
time in decades.

Having a machine-readable version of the Sketchpad code would by
itself be an immensely valuable thing for the study of the history of
computing.

## Software that Once Existed

We have seen mention of various pieces of TX-2 software, though we
don't currently have a copy of any of these:

1. Sketchpad by Ivan Sutherland; as noted above, there is a listing,
   but we would very much like to find a better-preserved one.
1. Sketchpad-III by Timothy Edward Johnson
1. The TX-2 BCPL compiler by Martin Richards, Henry Ancona et al.
1. [The LO Text
   formatter](https://apps.dtic.mil/sti/pdfs/ADA007824.pdf)
1. Bill Sutherland's program for the [on-line graphical specification
   of computer
   procedures](https://mit.primo.exlibrisgroup.com/discovery/fulldisplay?vid=01MIT_INST:MIT&search_scope=all&tab=all&docid=alma990002681740106761&lang=en&context=L&virtualBrowse=true)
1. The M4 assembler
1. The [APEX](documentation#apex) time-sharing executive

## Code for the TX-2 Simulator Itself

See [TX-2 Simulator Source Code](../code) for the source code. You can
[try it out directly in your browser](https://tx-2.github.io/demo/) or
[build it
yourself](https://github.com/TX-2/TX-2-simulator/blob/main/docs/build/web.md)
if you like.
