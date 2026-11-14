# Second-generation sequencing: how it works

Hand-drawn, interactive figures of the mechanisms behind short-read sequencing, following a sample from library prep to FASTQ files. Two chemistries are covered: **Illumina** (bridge amplification, sequencing by synthesis) and **Element AVITI** (rolling circle amplification, sequencing by avidity).

Open any page in a browser; keep the files in one folder so the buttons that link the pages work.

## Pages

| Page | What it shows |
|---|---|
| `index.html` | The cover: a map of the project. Second generation (short reads) runs from library prep through either chemistry to its sequencer; third generation (long reads) is marked as in preparation. |
| `library-prep.html` | How DNA becomes a library: fragment, end repair + A-tail, adapter ligation, clean-up, QC + pooling, denaturing. Two indexing routes side by side: index in the adapter (PCR-free) and index added by PCR. |
| `flowcell-closeup.html` | Illumina: an 8-lane flow cell and a patch of its surface at molecular scale. Hybridization to the P5/P7 lawn, first extension, bridge amplification into clusters, sequencing by synthesis with labelled blocked nucleotides, index reads, paired-end turnaround, and the files that come out. |
| `aviti-sequencing.html` | AVITI: a library circle lands on a surface primer, rolling circle amplification builds a polony (one long strand of tandem copies), then sequencing by avidity: an avidite binds many copies at once, is imaged in four channels, washed off, and an unlabelled blocked nucleotide steps the strand on by one. The signal path from camera image to base call is shown, with a card comparing the two chemistries. |
| `sequencer-flowcell.html` | A benchtop Illumina-style sequencer you can load and run, with a see-through view of the fluidics and optics. |
| `aviti-sequencer.html` | The AVITI-style instrument, two-sided: side A and side B each have a door, a flow cell stage, a chilled reagent cartridge, a selector valve, a syringe pump and a wash bottle, and can be loaded and run independently (300 cycles each, as 2 x 150). One imaging module (objective, camera, LEDs) rides a rail between the two stages and serves one side at a time, so a side that is ready to image while the other is being imaged waits. The box and bay layout approximate Element's instrument; the two-fluidics, one-imaging architecture is from Arslan et al. |

Drag to turn a figure, use the buttons in order, and switch on **Labels** (and **See-through** on the sequencer) to name the parts.

## Principles the figures try to make visible

- **Clonal amplification before reading.** One molecule is too dim to see, so every chemistry first makes a cluster or polony of identical copies: Illumina by bridge amplification (about a thousand separate strands), AVITI by rolling circle amplification (one strand carrying many tandem copies of the original circle, so a copying error is not passed on).
- **One base per cycle.** A reversible 3' block guarantees that each strand advances by exactly one nucleotide per cycle; the block is removed before the next cycle.
- **Reading by colour.** Four dyes, one per base. The camera photographs the whole surface each cycle, the brightest channel at each spot is the base, and the quality score reflects how clearly it won.
- **Reading and stepping can be separate steps.** In Illumina the labelled nucleotide that is read is also the one incorporated. In AVITI an avidite is read and then washed off, and a plain nucleotide does the stepping, which lets each step be optimised on its own.
- **Indexes and paired ends.** Barcodes in the adapters tell pooled libraries apart; reading the fragment from both ends gives paired reads.

## Sources and caveats

These are teaching sketches, not manufacturer documentation. Strand lengths are shortened, only a few cycles and amplification rounds are played, and the instrument is a generic design. The AVITI page follows Arslan et al., *Sequencing by avidity enables high accuracy with low reagent consumption*, Nat Biotechnol 2024, doi 10.1038/s41587-023-01750-7; details the paper does not give (the RCA enzyme, lane count, circularization chemistry) are inferred and marked as such on the page.

`src/` holds the figure sources; the pages at the top level are the built single-file versions.

Made with [Colorfigures](https://april-zhu.com/colorfigures) (MIT, see `LICENSE`).
