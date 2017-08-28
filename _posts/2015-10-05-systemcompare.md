---
layout: posts
title: Comparison of major computer synthesizer languages 2015
categories: notes
tag: synth
---

# Preface: things in common #

Modern music synthesis-composition language environments are deeply influenced by the concept of Max Mathew's MUSIC-N series.   In the Music-N system, a library of functions called unit generators (UGens, or opcodes) are built around signal processing and synthesis routines.  Then an instrument can be defined by constructing different UGens.   Then, another score file contains information such as frequency, duration, amplitude and others to generate the music piece.

Overall, the MUSIC-N model is still the basic concept among all different sound synthesizing/composing programming languages.  Due to limitation of the computation power from early computers, MUSIC-N did not provide real time performing or support MIDI when it was developed.  However as the computation power has been improved exponentially, most of computer synthesizing programming environments now support both MIDI and OSC controls for live and interactive performances.

# CSound #

Csound, as well as MUSIC-11, was originally developed in MIT by Barry Vercoe in 1986.  Vercoe followed MUSIC-N model initiated by Max Mathews at the Bell Labs.

Just like other MUSIC-N system, Csound devided sound synthesizing process into two modules: instrument and score.  Csound system also saves these two modules into two different (.orc and .sco) files for composers to be able to reuse and try different combinations.  In Csound unified file code (.csd), those two parts of modules are tagged within a markup language syntax.

The major strength of Csound is it is well integrated with major developing programming languages today such as C, C++, Python, Java, Lisp, and etc..  And the whole Csound programming environment can be run on the mobile system.

Early Csound does not support real time sound processing.  A music composition has to be rendered before it can be played back.  However, start from Csound 5 released in 2006, Csound starts to support MIDI and OSC as signal input to make real time performance or interactive performances possible.  Furthermore, in Csound 6 released in 2013, instruments and orchestras can be re-compiled at any time during a running performance.  It makes live coding on Csound possible.

Nevertheless, even though Csound has started supporting live performance, it does not provide functions that created GUI controls.  Therefore users has to depend on other environments for GUI controlling such as Max/MSP or Python. 



# Max/MSP and PureData #

Both Max/MSP and Pure Data was developed by Miller Puckette.  He developed Max in the mid-80s in IRCAM to provide composers with an graphic programming interface for interactive computer music.  Later because of disagreeing of the decision of Max became a closed system, Puckette released an redesigned an open sourced version called Pure Data in 1996.  Despite some minor difference between these two, they are very similar from each other.

Max and pd are both graphic programming environments.  All UGens and functions are designed to be an object boxes with inlets and outlets for users to achieve high level programming by patching those objects.  

# SuperCollider #

SuperCollider was released in 1996 by James McCartney for real time audio synthesis and algorithmic composition.

SuperCollider was designed to be expressive dynamic programming language to be played and controlled on real time.  The system structure is using server-client model.  The DSP module is handled on the server to make sure it's been played on real time.  The SuperCollider language (sclang) handler translates the language to OSC messages in order to control the SuperCollider DSP server (scsynth).  The scsynth is an independent sound generation application can be triggered without SuperCollider language.

The SuperCollider audio server supports any number of inputs and outputs for multichannel setups.  It applies a bus system to allow dynamically restructure of the signal flow.  The node tree system handles the structure of synthesis to define the order of execution.  Recently, a new server called Supernova has been introduced to support multi-processor computation. The sclang is a object-oriented programming language inherited from Smalltalk with a syntax of Lisp or C.  

Even though SuperCollider and it's server can be controlled by any other programs that sends OSC messages, supercollider also provides library for users to build GUI for their application.  Furthermore, recent research in Japan is creating a framework that allows SuperCollider programmer to create apps for iOS.

The main strength of SuperCollider is on it's server/client model.  Because the DSP server is an independent application controlled by OSC messages, it can receive and execute control messages from different computers via the internet even globally.  It can open a new possibility of music performance.

# Reaktor #

Reaktor is a graphical modular software music studio developed my Native Instruments in 1996.  Users can combine or use it's preset modules to build their own synthesizer instruments, samplers, effects and sound design tools. As a commercial software, it supplies many factory preset libraries of instruments and effects, from emulations of classic synthesizers to futuristic sound design tools.  In addition Reaktor also has an active community that users build their own libraries for different purposes e.g. DJ platforms. 

Reaktor can work as an independent application or plugin within a DAW software, it's graphical patching interface gives users freedom to patch different synthesis modules like modular synthesizers.  Modules can also be categorized into hierarchy for better patching management.  Users can start tweaking modules by editing factory preset objects.  Also, building GUI within Reaktor is easy with it's build-in graphical contents or use custom designed look and feel of their instruments. 

Besides MIDI control as input source. The new version of Reaktor supports OSC messages as input sources, users can use any OSC controllers or sensors to control or interact with Reaktor instruments.  However because Reaktor is a closed environment, it does not provide user defined mapping algorithms for controlling.  It's using standard 0-127 midi values for parameter controls.

The strength is Reaktor is it's rich library and sound bank are ready to use for users and sound designers.  Reaktor instruments, libraries, ensembles can only be executed within Reaktor environment, it can not be compiled to a standalone application or mobile app.

# Chuck #

Chuck is a strongly time based audio programming language for real time synthesis, composition and performance by Ge Wang in 2003.  Chuck programming language is loosely C like but in a concurrent scheme, which means the output of a function is on the right side of code.  The benefit of this programming design is to be able to create a stream of functions quickly with less codes. Besides unit generators, Chuck also provides unit analyzers for research and feature extractions.

The down side of Chuck is in it's real time based programming environment. It does not separate sampling rate of audio and controlling signals.  Even though it makes coding a lot easier and faster it sacrifices the computing power of your system.  Chuck has been criticized for being unstable as a programming environment. 

# impromptu #

Impromptu is a programming environment designed for live coding by Andrew Sorensen in 2006.  It also contains sound synthesis modules and unit generators.  Sound modules, variables and functions can be redefined and changed to take effect immediately.  There is also scheduling in Scheme for composers to code events to be executed on distinated time. Furthermore it can work as a host of plug-in AU instruments and use them for audio synthesis and effects.  It also allows users to directly program for videos with live coding.

The language used in Impromptu is based on Scheme.  In order to solve the typing speed problems, Impromptu has functions for pasting pre determined texts to shorten typing time.  

Impromptu is designed for live coding audio and video and being executed and changed in real time.  The program written in Impromptu can not be compiled onto other platforms.