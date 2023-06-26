# j6n55
## Background
This document will outline the process I went through in building my very own keyboard from scratch.
## Goals
## Parts & Cost
| Part                   | Cost (CAD) |
|------------------------|------------|
| RPi Pico               | 12.95      |
| Copper Wiring          |            |
| Soldering Kit          |            |
| Switches (KTT Kang V3) | 25.87      |
| Kaihl Hotswap Sockets  | 17.29      |
| Total Cost (WIP)       | 56.11      |
## Layout
I initially found [keyboard-layout-editor](http://www.keyboard-layout-editor.com/), where I viewed existing layouts and played around with creating my own layouts. For this project, my goal was to create a smaller form factor keyboard than my current 60%.

## Working with QMK
### Setup
Setup of qmk was fairly straight-forward, following the available [documentation](https://docs.qmk.fm/#/newbs_getting_started).
```
pip3 install --user qmk
echo 'PATH="$HOME/.local/bin:$PATH"' >> $HOME/.zshrc && source $HOME/.zshrc
qmk setup
qmk compile -kb clueboard/66/rev3 -km default
```
### QMK Configuration
I realized I would not be able to reuse the raw data I created earlier in `keyboard-layout-editor`, so I looked to port over my layout to qmk configuration.

I forked the `qmk_firmware` repo to include my new layout & created a keyboard profile for myself.
```
qmk new-keyboard
...
qmk compile -kb handwired/j6n55 -km default
```
The changes I made can be viewed [here](https://github.com/qmk/qmk_firmware/compare/master...j6nca:qmk_firmware:j6n55).