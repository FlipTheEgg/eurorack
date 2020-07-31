# HelloWorld

WIP

Hello World! This is a three-channel eurorack mixer based on the schematic of the [AI Synthesis AI002](http://aisynthesis.com/ai002-diy-eurorack-mixer-module-build/), but more importantly, as the name suggests, this is my first time doing several things. It's my first time...
 - Using KiCad
 - Making a eurorack module
 - Making something usable enough to give to someone (or maybe even sell)
 
I learned a lot in this process, and I wanted to document those experiences - for myself as well as others that could be interested in learning the same. 

If you're just here to make the module, go ahead and skip to [Can I make this?](https://github.com/FlipTheEgg/eurorack/tree/master/HelloWorld#can-i-make-this).
 
 ## How did I  do it?

I wanted to start out simple, so I chose a schematic i *completely* understood: a simple mixer with a volume control. AI Synthesis has a wonderful selection of well-documented DIY builds, including schematics and build guides, and I chose to copy the AI002 because the challenge with this project wasn't circuit design, but learning KiCad and designing to the specifications of Eurorack. My goal over time is to simultaneously design more sophisticated PCBs, and learn about more advanced circuits as I go.

With this specific project in mind I followed the guide [Getting Started in KiCad](https://docs.kicad-pcb.org/5.1/en/getting_started_in_kicad/getting_started_in_kicad.html), and substituted the example project with the AI002. I've previously experimented with [Fritzing](https://fritzing.org/), but I found it a little inaccurate and inflexible. Following the guide mostly went well and without issue. Not all the components I wanted to use had footprints in the standard Kicad library, but I managed to select some different components, or make my own footprints, which the guide also covers. I found KiCad to be slightly bulky to use at first, especially the disconnect between schematic symbol and footprint seemed cumbersome until I understood the flexibility this gives. I also had some confusion about how KiCad connects legs of the schematic components to the pins of the footprint (I can easily choose a 16-pin footprint to a 4-pin schematic component, for example), but  I realized that's where knowing how to edit footprints is really important and powerful. This also encouraged me to check the datasheets for my components whenever I was in doubt, which is good! The guide actually did answer almost all my questions, and upon revising my design, some of these quirks made more sense to me. For example, going back and choosing a different footprint or schematic symbol for a component, which I did a couple of times, was very quick and painless.

I also decided to design the panel as a PCB. I've seen this done on commercially available modules, and I think it looks good and seems both economical and practical. So I drew up a panel beside the main PCB (open the file HelloWorld.kicad_pcb to see how I did this), and followed the [Doepfer A100 Mechanical specification](http://www.doepfer.de/a100_man/a100m_e.htm) to see how to make the panel. I noticed that a lot of existing modules have oval mounting holes, which seemed smart. I also noticed that the Doepfer page said nothing about how tall my main PCB could be. Both of these problems were solved by measuring images of other modules on my screen, and calculating the length according to the known panel dimensions. This is not reccomended, *do* steal my findings from my schematics. I alsom made a custom footprint for the oval holes, as well as the holes for the potentiometers and the jacks. I might share these on GitHub at some point. Next time I think I'd like to make the PCB half a mm taller, so the offset, measured from the top and the bottom of the PCB, can be measured in whole mm's in relation to the panel. More on this measurement circus later. I later learned that having two boards in one file isn't as easy as I thought. KiCad handles it fine, but making it with a little breakoff part was incredibly difficult, and I couldn't figure it out. So I had to copy the main file, and make one file for the PCB and one for the panel. See (link...)

I realized that I needed a way to organize my Bill Of Materials (BOM) to keep track of what I needed to buy, so I made a spreadsheet where I listed and sourced my components, as well as held some other notes. This file is included in this repository, but it is a bit messy. I've deliberatly not cleaned it up, to give you an insight into how I worked. This process will likely be refined somehow. I chose to source my components at [Tayda](https://www.taydaelectronics.com/) and [Thonk](https://www.thonk.co.uk/) - more info in the BOM file.

Lastly I plotted the PCB to gerber files, ready to be manufactured, according to [the handy guide](https://support.jlcpcb.com/article/44-how-to-export-kicad-pcb-to-gerber-files) provided by my PCB manufacturer of choice, [JLCPCB](https://jlcpcb.com/). I reccommend following the guide for whereever you get them produced, it seems like they all have a lot of helpful information to help you to order correctly. I chose a black, Lead-free HASL board. Having the solder lead-free brought up the price a bit, but not by much. I made two seperate orders, one for the main board, and one for the panel, and ordered them together, choosing "europacket" as my shipping method. I'll report how it goes!

## What did I learn?
Here are some experiences I had, and some mistakes that I don't plan on repeating.
### Mils
While laying out the PCB, i quickly noticed that the standard grid wasn't in millimeters, but in [mils](https://en.wikipedia.org/wiki/Thousandth_of_an_inch). A mil is a thousandth of an inch, and 1 mil = 0.0254mm - making 10 mil just barely more than a quarter of a mm. This is apparently for historical reasons, but a lot of components are laid out with mil spacing between pins. I read somewhere that it has something to do with the tooling of PCB manufacturers, but I'm not really sure. What it meant for me, though, was that I had to change the grid to mm. The Doepfer eurorack standard is defined in millimeters, and some of the components are measured in mils, so that's a bit annoying. I prioritized  setting millimeter spacings between externals - jacks, pots - and place the rest in mils. If I place the other components in mm, I can't align my IC and my caps properly, which annoys me. So there was a bit of switching back and forth, but all in all it was OK.

### Footprints: decide what components to use *before* you layout.
This one I only thought about when shopping for components! I chose the footprints before I decided the exact components. This meant that when it came to decide what those were, I had accidentally limited my choice. In this case, it meant that I couldn't use box-type capacitors, because they have a much larger pin spaceing than I had selected. It also meant that I couldn't use a shrouded header for the power connector as originally planned, because I placed it too close to the edge without concern for its actual size. Speaking of the power header, I put it in the corner due to the Doepfer spec saying to place it there, but after looking at several popular modules I can conclude that the placement doesn't really matter. None of this was a problem, but I can easily imagine making an error like this resulting in having to redo the entire layout. Speaking of condensers, I just wanna plug [this great blogpost](http://tagboardeffects.blogspot.com/p/components.html) by Tagboardeffects about components. I've used it to understand especially what the differences are between condensers. Next time I'll try importing the [DigiKey Kicad Footprint Library](https://www.digikey.com/en/resources/design-tools/kicad), as I've read good things about it, and see if that helps.

### File structure and you: This repository is a mess...
...but it doesn't have to be this way! 
A lot of the confusion in the repository comes from how I exported the gerbers. I made seperate folders for the gerber files (smart), but put the zips outside of those folders (dumb). Next time I'll do it like this:

> **ProjectName**
>> other stuff
>>
>> **gerbers**
>>> FolderWithMainboard
>>>
>>> FolderWithPanel
>>>
>>> Mainboard.zip
>>>
>>> Panel.zip

I also have some redundancy on top of that, because I have a PCB file for the panel and the mainboard seperately, **AND** a file for both of them, du to how I split them originally. Next time I'll make a seperate PBC file for the panel from the get-go.

### Measure twice: Building the PCB before the panel is bad.
I accrued some technical debt by designing the PCB without having a plan for the placement of the components. When I was completely done with the main board, I had to measure where the jacks and pots went on the panel, correcting for the different sizes of the two. Luckily KiCad has a neat built-in ruler, but I had to make a lot of measurements. In the future, I'd vastly prefer placing the jacks and pots prior to designing the PCB.

### Panel design.
I really like the aesthetic of using a PCB as the panel, but there's room for improvement here. Using custom footprints, and clever design, you can do [some pretty incredible stuff](https://www.andrewsowa.com/sir-james-condi/). I'd like to start designing my panels using [Inkscape](https://inkscape.org/), and include custom graphics and logos and such, but I found it a bit difficult to also learn to use Inkscape i parallel. I did however find two promising tools for accomplishing this: [Svg2Shenzen](https://github.com/badgeek/svg2shenzhen) and [Synth Panels Designer](http://synthpanels.design/), both are plugins for Inkscape. Svg2Shenzen assists in managing the PCB layers and exporting to KiCad, and Synth Panels Designer helps make good looking scales for sliders and knobs, as well as having presets for panels in the correct sizes. I look forward to start designing better panels.

## Can I make this?
Yeah, go ahead! I wrote CC-BY-SA on the board, so I'm sticking with that. I don't know if this is the best license choice for this, if you know a bunch about it do reach out, I'd appreciate it. Send the gerber zip files to JLCPCB or someone else, and read the BOM to find out what parts you need, and order them somewhere. But **Don't** send them the zip with the panel *and* the main PCB, that'll go wrong. If you somehow do, please send me an image of the board you recieve.

## Resources: 
 - [KiCad](https://kicad-pcb.org/)
 - [Getting Started in KiCad](https://docs.kicad-pcb.org/5.1/en/getting_started_in_kicad/getting_started_in_kicad.html)
 - [AI Synthesis AI002 build guide](http://aisynthesis.com/ai002-diy-eurorack-mixer-module-build/) Schematic is under "resources".
 - [Befaco](https://www.befaco.org/) also has the schematics available for all their modules. They're all significantly more advanced than this build, but I'll definitely be looking at them in the future!
 - [Doepfer A100 electrical specification](http://www.doepfer.de/a100_man/a100t_e.htm)
 - [Doepfer A100 mechanical specification](http://www.doepfer.de/a100_man/a100m_e.htm)
 - [Tayda Electronics](https://www.taydaelectronics.com/) for parts
 - [Thonk](https://thonk.co.uk/) for more parts
 - [JLCPCB](https://jlcpcb.com/) for PCB manufacture
 - [How to export KiCad PCB to Gerber files](https://support.jlcpcb.com/article/44-how-to-export-kicad-pcb-to-gerber-files)
 - [Tagboardeffects - "Components"](http://tagboardeffects.blogspot.com/p/components.html)
 - [Inkscape](https://inkscape.org/)
 - [Svg2Shenzen](https://github.com/badgeek/svg2shenzhen)
 - [Synth Panels Designer](http://synthpanels.design/)
 - [DigiKey footprint library](https://www.digikey.com/en/resources/design-tools/kicad)
