# DNA Sequencing Technologies: Mechanisms and Workflows

Interactive, hand-drawn three-dimensional figures of first-, second- and third-generation DNA sequencing, following a sample from extracted DNA to the sequence files delivered to the compute cluster (Farm, UC Davis), one page per step. Covered: a Sanger sketch (first generation); two short-read chemistries, **Illumina** (bridge amplification, sequencing by synthesis) and **Element AVITI** (rolling circle amplification, sequencing by avidity); and two long-read chemistries, **PacBio HiFi** (single-molecule real-time sequencing in zero-mode waveguides, circular consensus) and **Oxford Nanopore** (a motor protein feeds a strand through a pore; the current trace is the read).

**Status.** The second-generation pages (library preparation, Illumina, AVITI) have been reviewed against the cited sources. The third-generation pages (PacBio HiFi, Oxford Nanopore) and the Sanger page are **drafts under review and not yet fully verified**; they are published so that they can be examined, each carries a "Draft" badge, and the nanopore flow cell page requires further detail. Their figures should be treated as provisional until this notice is removed.

This is a personal study project: my own notes, drawn as figures. It is not teaching material and not manufacturer documentation; corrections are welcome.

Live site: https://w1shyoubest.github.io/dna-sequencing-technologies/

Open any page in a browser; keep the files in one folder so the buttons that link the pages work. Drag to turn a figure, use the buttons in order, and switch on **Labels** (and **See-through** on the sequencers) to name the parts.

## Folder layout

```
index.html                     the overview page (start here)
1st-generation/
  sanger/sanger.html           Sanger sequencing (preliminary sketch)
2nd-generation/
  library-prep.html            short-read library preparation, shared by both platforms
  illumina/flow-cell.html      Illumina flow cell: bridge amplification, sequencing by synthesis
  illumina/sequencer.html      Illumina-style benchtop sequencer
  aviti/flow-cell.html         AVITI flow cell: rolling circle amplification, sequencing by avidity
  aviti/sequencer.html         AVITI-style two-sided sequencer
3rd-generation/                (drafts, under review)
  pacbio/library-prep.html     SMRTbell library preparation
  pacbio/smrt-cell.html        SMRT Cell and zero-mode waveguide
  pacbio/sequencer.html        Revio-style sequencer
  nanopore/library-prep.html   nanopore library preparation (ligation and native barcoding)
  nanopore/flow-cell.html      flow cell priming and loading; a single pore reading
  nanopore/devices.html        MinION and PromethION
src/                           figure sources in the same layout, plus core.js
```

Each page in a platform folder is self-contained (the drawing engine is built in); keep the folders together so the navigation buttons between pages work.

## Pages

| Page | What it shows |
|---|---|
| `index.html` | The cover: a map of the project. Library prep branches into the Illumina and AVITI routes, each ending at its own instrument. The bookends (DNA extraction, files to the cluster) and third-generation sequencing are marked as in preparation. |
| `1st-generation/sanger/sanger.html` | Sanger sequencing, a first sketch: chain termination with dye ddNTPs, capillary electrophoresis past a laser window, the chromatogram. Draft. |
| `2nd-generation/library-prep.html` | How DNA becomes a library: fragment, end repair + A-tail, adapter ligation, clean-up, QC + pooling, denaturing. Two indexing routes side by side: index in the adapter (PCR-free) and index added by PCR. |
| `2nd-generation/illumina/flow-cell.html` | Illumina: a flow cell and a patch of its surface at molecular scale. Hybridization to the P5/P7 lawn, first extension, bridge amplification into clusters, sequencing by synthesis with labelled blocked nucleotides, index reads, paired-end turnaround, and the files that come out. |
| `2nd-generation/illumina/sequencer.html` | A benchtop Illumina-style sequencer you can load and run (2 x 150 = 300 cycles), with a see-through view of the fluidics and optics. Links across to the AVITI instrument. |
| `2nd-generation/aviti/flow-cell.html` | AVITI: a library circle lands on a surface primer, rolling circle amplification builds a polony (one long strand of tandem copies), then sequencing by avidity: an avidite binds many copies at once, is imaged in four channels, washed off, and an unlabelled blocked nucleotide steps the strand on by one. The signal path from camera image to base call is shown, with a card comparing the two chemistries. |
| `2nd-generation/aviti/sequencer.html` | The AVITI-style instrument, two-sided: side A and side B each have a door, a flow cell stage, a chilled reagent cartridge, a selector valve, a syringe pump and a wash bottle, and run independently (300 cycles each, as 2 x 150). One imaging module rides a rail between the two stages and serves one side at a time; a side that is ready to image while the other is being imaged waits. Links across to the Illumina instrument. |
| `3rd-generation/pacbio/library-prep.html` | **Draft.** PacBio HiFi library prep (SMRTbell prep kit 3.0), DNA only, starting from extracted HMW DNA (the kit's optional short-read eliminator acts on genomic DNA and is treated as part of extraction QC): shearing to 15-20 kb, repair + A-tailing, hairpin SMRTbell adapters on both ends (the insert becomes one closed single-stranded circle), nuclease treatment of anything with a free end, AMPure size selection + QC, then primer annealing and polymerase binding. |
| `3rd-generation/pacbio/smrt-cell.html` | **Draft.** A SMRT Cell and one zero-mode waveguide cut open: the polymerase fixed to the glass floor, the lit zone at the bottom of the 70 nm hole, phospholinked nucleotides whose dye on the terminal phosphate flashes while held and leaves on incorporation, the real-time trace (pulse = base, gap = kinetics, long gap at 5mC), subreads from each pass round the circle, and the HiFi consensus read. |
| `3rd-generation/pacbio/sequencer.html` | **Draft.** A Revio-style instrument: SMRT Cell tray and sequencing plate on the work deck, a robot moving cells to four independent stages, lasers and a camera under each, onboard GPUs building HiFi reads and calling methylation; cells can start while others run. |
| `3rd-generation/nanopore/library-prep.html` | **Draft.** Oxford Nanopore library prep by ligation, DNA only, two kits side by side: the Ligation Sequencing Kit (one sample: end-prep + nick repair, Y adapter with motor protein and tether straight on) and the Native Barcoding Kit (a barcode on each sample, pool, then the native adapter). Optional fragmentation or size selection first; clean-up with Long or Short Fragment Buffer; priming and loading. |
| `3rd-generation/nanopore/flow-cell.html` | **Draft.** A MinION flow cell (FLO-MIN114) with the full priming and loading protocol as nine steps: flow cell check, open the priming port, draw back 20-30 uL to clear the bubble, 800 uL priming mix, mix the 75 uL library, open SpotON and 200 uL more through the priming port, 75 uL dropwise onto SpotON, close and fit the light shield, start. Beside it one sensor well cut open: membrane, pore, electrode, the tethered library with its motor protein feeding a strand through, the ion current; cards show the flow cell check, the channel trace and the basecalls. |
| `3rd-generation/nanopore/devices.html` | **Draft.** MinION Mk1D on a laptop and a PromethION 24 side by side, with a comparison card (flow cells, channels and minimum pores, output, run time, basecalling, size), insertion and run animations, and a see-through of the ASIC, Peltier and GPU compute. |

## Principles the figures try to make visible

- **Clonal amplification before reading.** One molecule is too dim to see, so every chemistry first makes a cluster or polony of identical copies: Illumina by bridge amplification (about a thousand separate strands), AVITI by rolling circle amplification (one strand carrying many tandem copies of the original circle, so a copying error is not passed on).
- **One base per cycle.** A reversible 3' block guarantees that each strand advances by exactly one nucleotide per cycle; the block is removed before the next cycle.
- **Cycles.** One cycle reads one base on every cluster or polony. Kits are named by the total: a 2 x 150 paired-end run is a 300-cycle run, 150 per read. Both sequencer pages count this way.
- **Reading by colour.** Four dyes, one per base. The camera photographs the whole surface each cycle, the brightest channel at each spot is the base, and the quality score reflects how clearly it won.
- **Reading and stepping can be separate steps.** In Illumina the labelled nucleotide that is read is also the one incorporated. In AVITI an avidite is read and then washed off, and a plain nucleotide does the stepping, which lets each step be optimised on its own and is the main reason for its lower error rate.
- **Indexes and paired ends.** Barcodes in the adapters tell pooled libraries apart; reading the fragment from both ends gives paired reads.

## Verification & Inference

These are study sketches, not manufacturer documentation. Strand lengths are shortened, only a few cycles and amplification rounds are played, and both instruments are drawn smaller and simpler than life.

**AVITI, from Arslan et al., *Sequencing by avidity enables high accuracy with low reagent consumption*, Nat Biotechnol 42, 132–138 (2024; online May 2023), doi 10.1038/s41587-023-01750-7:** libraries circularized before loading (Adept kit), denatured, loaded at 8 pM and hybridized to the flow cell; rolling circle amplification on the instrument giving about 1 billion polonies per flow cell; avidites built on a dye-labelled streptavidin core with about three nucleotide arms; an engineered polymerase for binding and a separate one for the unlabelled, blocked stepping nucleotide; four colours; 96.2% of bases above Q30 and 85.4% above Q40; reads of 2 x 150 and 1 x 300; two flow cells served by two fluidics modules and one shared imaging module.

**AVITI, from Element's specification sheet and product pages:** dual flow cells controlled independently ("like having two sequencers in one"); each flow cell a two-lane glass substrate in a plastic cartridge; kits from 2 x 75 to 2 x 300; at least 1 billion read pairs per flow cell; 2 x 150 high output in about 38 hours; instrument 29.5 x 37.6 x 28.5 in (H x W x D), 155 kg. Circularization can be done in a tube (Adept and Elevate kits) or on the flow cell with Cloudbreak Freestyle chemistry, which also takes Illumina TruSeq and Nextera adapter libraries directly.

**Inferred, not published:** the identity of the RCA polymerase (drawn as a phi29-type strand-displacing enzyme), the surface chemistry of on-flow-cell circularization, whether the optics or the stages move between the two sides (the figure moves the optics), and the internal layout of both instruments.

**PacBio, from PacBio's "How HiFi sequencing works" page and the Revio page:** SMRTbell circular templates; single-molecule real-time reading in SMRT Cells with millions of wells; HiFi reads typically 15-25 kb at Q30+ (99.9%) from circular consensus, with no PCR; base modifications called from polymerase kinetics; Revio: four stages (up to four SMRT Cells at once), 12-30 h per cell by insert size, 70-120 Gb HiFi per cell for 10-25 kb inserts, up to 480 Gb/day, 99.95% (Q33) read accuracy, onboard NVIDIA GPUs with DeepConsensus, 92.7 x 91.4 x 174.5 cm, 465 kg. ZMW geometry (~70 nm wide, ~100 nm deep, aluminium on silica, ~20 zL observation volume) and the phospholinked-nucleotide chemistry are from Eid et al., Science 2009, and Levene et al., Science 2003. The library steps follow PacBio procedure checklist 102-166-600 (SMRTbell prep kit 3.0). **Inferred:** the Revio's internal layout (robot, stage and optics placement), the exact pass count behind a given Q score, and the schematic trace.

**Nanopore, from ONT's "Ligation sequencing gDNA V14" and "Native barcoding gDNA V14" protocols:** DNA repair and end-prep (NEBNext FFPE repair + Ultra II end-prep), native barcode ligation and pooling (barcoding kit only), adapter ligation, bead clean-up with Long or Short Fragment Buffer, flow cell priming and loading with sequencing buffer and library beads. The motor protein and tether on the adapter arms are from ONT's published description of the ligation adapter. The flow cell loading steps and volumes (priming mix 1170 uL FCF + 5 uL BSA + 30 uL FCT; draw back 20-30 uL; 800 then 200 uL through the priming port; 37.5 uL SB + 25.5 uL LIB + 12 uL library = 75 uL dropwise onto SpotON; light shield) and the warranty minimums (800 pores MinION/GridION, 5000 PromethION) are from the same ONT protocol. Device facts from ONT product pages: MinION Mk1D 55 x 13 x 125 mm, 130 g, USB-C, Peltier control for 10-35 C ambient; PromethION 24 runs up to 24 independent flow cells, 72 h runs, onboard GPUs, each PromethION flow cell about six times a MinION flow cell. **Inferred or widely quoted rather than from an ONT page I fetched:** 512 channels / 2048 wells per MinION flow cell and 2675 channels per PromethION flow cell, four wells per channel with a mux scan, ~180 mV bias and ~5 kHz sampling, the CsgG-derived R10.4.1 pore with two reader heads, the native barcoding order (barcode, pool, adapter), loading-sheet and screen numbers, and the devices' internal layouts.

**Illumina:** the flow cell is drawn with 8 lanes (the HiSeq layout; MiSeq has 1, NextSeq 4, NovaSeq 2 or 4) and the instrument is a generic benchtop design. Cartridge well names are by function, not a real well map.

`src/` holds the figure sources in the same folder layout; the pages outside `src/` are the built single-file versions.

Made with [Colorfigures](https://april-zhu.com/colorfigures) (MIT, see `LICENSE`).
