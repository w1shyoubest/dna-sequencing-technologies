# Illumina sequencing, as interactive figures

Three hand-drawn, interactive pages that follow a sample from library prep to FASTQ files. Open any of them in a browser; keep the files in one folder so the buttons that link the pages work.

| Page | What it shows |
|---|---|
| `library-prep.html` (also `index.html`) | How DNA becomes a library: fragment, end repair + A-tail, adapter ligation, clean-up, QC + pooling, denaturing. Two indexing routes side by side: index in the adapter (PCR-free) and index added by PCR. |
| `flowcell-closeup.html` | An 8-lane flow cell and a patch of its surface at molecular scale: hybridization to the P5/P7 lawn, first extension, bridge amplification, sequencing by synthesis, index reads, paired-end turnaround, and the files that come out. |
| `aviti-sequencing.html` | Element AVITI for comparison: library circle, rolling circle amplification into a polony, sequencing by avidity (bind, image in four channels, call, wash, step), with the signal path from camera image to base call. Based on Arslan et al., Nat Biotechnol 2024. |
| `sequencer-flowcell.html` | A benchtop sequencer you can load and run, with a see-through view of the fluidics and optics. |

Drag to turn a figure, use the buttons in order, and switch on **Labels** (and **See-through** on the sequencer) to name the parts.

These are teaching sketches, not manufacturer documentation. Strand lengths are shortened, only a few cycles and amplification rounds are played, and the instrument is a generic design.

`src/` holds the figure sources; the pages at the top level are the built single-file versions.

Made with [Colorfigures](https://april-zhu.com/colorfigures) (MIT, see `LICENSE`).
