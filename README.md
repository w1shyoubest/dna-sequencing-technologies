# Tissue to Farm

Hand-drawn, interactive figures that follow a sample from DNA to the FASTQ files that land on the cluster, one page per step. Two short-read chemistries are covered: **Illumina** (bridge amplification, sequencing by synthesis) and **Element AVITI** (rolling circle amplification, sequencing by avidity).

This is a personal study project: my own notes, drawn as figures. It is not teaching material and not manufacturer documentation; corrections are welcome.

Live site: https://w1shyoubest.github.io/second-generation-sequencing/

Open any page in a browser; keep the files in one folder so the buttons that link the pages work. Drag to turn a figure, use the buttons in order, and switch on **Labels** (and **See-through** on the sequencers) to name the parts.

## Pages

| Page | What it shows |
|---|---|
| `index.html` | The cover: a map of the project. Library prep branches into the Illumina and AVITI routes, each ending at its own instrument. The bookends (DNA extraction, files to the cluster) and third-generation sequencing are marked as in preparation. |
| `library-prep.html` | How DNA becomes a library: fragment, end repair + A-tail, adapter ligation, clean-up, QC + pooling, denaturing. Two indexing routes side by side: index in the adapter (PCR-free) and index added by PCR. |
| `flowcell-closeup.html` | Illumina: a flow cell and a patch of its surface at molecular scale. Hybridization to the P5/P7 lawn, first extension, bridge amplification into clusters, sequencing by synthesis with labelled blocked nucleotides, index reads, paired-end turnaround, and the files that come out. |
| `sequencer-flowcell.html` | A benchtop Illumina-style sequencer you can load and run (2 x 150 = 300 cycles), with a see-through view of the fluidics and optics. Links across to the AVITI instrument. |
| `aviti-sequencing.html` | AVITI: a library circle lands on a surface primer, rolling circle amplification builds a polony (one long strand of tandem copies), then sequencing by avidity: an avidite binds many copies at once, is imaged in four channels, washed off, and an unlabelled blocked nucleotide steps the strand on by one. The signal path from camera image to base call is shown, with a card comparing the two chemistries. |
| `aviti-sequencer.html` | The AVITI-style instrument, two-sided: side A and side B each have a door, a flow cell stage, a chilled reagent cartridge, a selector valve, a syringe pump and a wash bottle, and run independently (300 cycles each, as 2 x 150). One imaging module rides a rail between the two stages and serves one side at a time; a side that is ready to image while the other is being imaged waits. Links across to the Illumina instrument. |

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

**Illumina:** the flow cell is drawn with 8 lanes (the HiSeq layout; MiSeq has 1, NextSeq 4, NovaSeq 2 or 4) and the instrument is a generic benchtop design. Cartridge well names are by function, not a real well map.

`src/` holds the figure sources; the pages at the top level are the built single-file versions.

Made with [Colorfigures](https://april-zhu.com/colorfigures) (MIT, see `LICENSE`).
