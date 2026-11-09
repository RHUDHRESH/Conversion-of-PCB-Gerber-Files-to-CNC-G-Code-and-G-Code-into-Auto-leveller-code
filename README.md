# PCB Milling G-code: Gerber to CopperCAM to AutoLeveller

G-code files for engraving, drilling and cutting a PCB for an automatic street light control circuit. The files were produced with CopperCAM and then passed through AutoLeveller. This is the Experiment 5 lab work from an electronics course.

**Stack:** CopperCAM (ISO-mill output), AutoLeveller 0.7.7 (Mach3 mode), G-code (`G21`, `G31` probe moves, `G92` zeroing).

## What it does

- Contains CopperCAM G-code for the four machining passes: engraving (`eng.txt`), drilling at 0.8 mm (`drill0.8.txt`), drilling at 1.2 mm (`drill1.2.txt`) and board outline cutting (`cut.txt`).
- Contains AutoLeveller versions of each file (`ALeng.tap`, `ALdrill0.8.tap`, `ALdrill1.2.tap`, `ALcut.tap`). These add probe-based height correction across the board.
- Lists the tools in the headers: a 3.17 mm engraver, 0.8 mm and 1.2 mm drills, and a 3 mm cutter.
- Gives the workpiece size in the headers: 32.69 x 27.93 x 0.1 mm.
- Documents the procedure in `exp5_formatted.docx`.

## Quick start

There is no build or install step. The `.tap` and `.txt` files are run on a CNC mill controller.

1. Check the board size and tool diameters against the file headers.
2. Follow `exp5_formatted.docx` for the CopperCAM and AutoLeveller steps.
3. The lab record applies auto-levelling to the engraving file. This repository also has leveled drill and cut files. Choose the set you need.

**Before you run any file:** the headers say a working probe is required, and the tool must be within 10 mm of the copper board for the first probe. These files were made for one board and one machine setup. Check the zero, tool and probe setup on your own machine first.

## How it works

```
PCB design (Gerber + drill + cut layers)   not included in this repository
   -> CopperCAM: set pads, drill sizes, origin and offset; calculate contours
   -> ISO-mill G-code: eng.txt, drill0.8.txt, drill1.2.txt, cut.txt
   -> AutoLeveller 0.7.7 (Mach3 mode): probe grid, leveled output
   -> AL*.tap files
```

## Project structure

```
.
├── eng.txt, drill0.8.txt, drill1.2.txt, cut.txt   # CopperCAM G-code
├── ALeng.tap, ALdrill0.8.tap, ALdrill1.2.tap, ALcut.tap   # AutoLeveller output
└── exp5_formatted.docx                            # Experiment 5 lab record
```

## Roadmap

- The G-code files for all four passes are present, both raw and leveled.
- Not included: the Gerber and drill source files, and the CopperCAM and AutoLeveller project files.
- The repository has no record of a machined board or a test cut.

## License

No LICENSE file is included. The `.tap` files carry AutoLeveller's GPLv2 notice in their headers.

---

Built by [Rhudhresh R](https://github.com/RHUDHRESH)
