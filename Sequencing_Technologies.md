# Sequencing Technologies for Microbial Genomics
## Sanger vs. NGS vs. Long-Read Sequencing

**Microbial Genomics Journey Workshop – Ghana 2026**
**Instructor: Ahmed M. Moustafa**

---

## Why Does Sequencing Technology Matter?

The sequencing platform you choose directly shapes what questions you can answer. A 5 Mb bacterial genome is small compared to human, but the questions we ask — outbreak tracking, resistance detection, mobile element characterization — demand specific strengths from different technologies.

**Key question before every experiment:** *What biological question am I trying to answer?*

---

## The Three Generations at a Glance

| Feature | Sanger | Short-Read NGS (Illumina) | Long-Read (ONT / PacBio) |
|---------|--------|--------------------------|--------------------------|
| Read length | 700–1,000 bp | 150–300 bp (paired-end) | 10,000–100,000+ bp |
| Accuracy (raw) | ~99.9% | ~99.9% | ONT: ~95–99%; PacBio HiFi: ~99.9% |
| Throughput | 1 read/reaction | Millions–billions of reads | Thousands–millions of reads |
| Cost per genome (bacterial) | Prohibitive for WGS | ~$70 | ~$90–200 |
| Time to data | ~2–4 hours | ~12–48 hours | ONT: minutes to hours; PacBio: hours |
| Key strength | Gold-standard accuracy, targeted | High throughput, low cost | Resolves repeats, structural variation, methylation |

---

## 1. Sanger Sequencing (First Generation)

### When to Use It in Microbial Genomics
- **Confirmatory sequencing**: Verify a mutation found by NGS
- **Single-gene typing**: 16S rRNA gene for species identification
- **MLST (traditional)**: Sequencing 7 housekeeping gene fragments
- **Plasmid insert verification**: Confirming cloned constructs
- **Small-scale studies**: When you have 1–10 isolates and one target gene

### Limitations
- Not practical for whole-genome sequencing of bacteria
- Low throughput — one gene at a time
- Cost per base is very high compared to NGS

---

## 2. Short-Read NGS (Second Generation)

### Illumina: The Workhorse

#### How It Works
- Library preparation: fragment DNA, add adapters
- Bridge amplification on a flow cell → clusters
- Sequencing by synthesis (SBS) — fluorescent reversible terminators
- Millions of reads in parallel

#### Key Platforms for Microbiology

| Platform | Output | Best For |
|----------|--------|----------|
| iSeq 100 | ~1.2 Gb | Small labs, targeted panels, teaching |
| MiSeq | ~15 Gb | Bacterial WGS (1–20 genomes), amplicon sequencing |
| NextSeq 550/1000/2000 | ~30–360 Gb | Medium-scale WGS, metagenomics |
| NovaSeq 6000/X | ~1–16 Tb | Large-scale surveillance, thousands of genomes |

#### Typical Bacterial WGS Workflow
1. DNA extraction (< 1 day)
2. Library prep — Illumina DNA Prep (Flex) or Hackflex (~2–3 hours)
3. Sequencing — MiSeq 2×250 bp or 2×300 bp (~24–48 hours)
4. Data output — ~50–100× coverage per genome (~500 Mb per genome)

### Use Cases in Bacterial Genomics

#### Outbreak Investigation & Surveillance
- SNP-based phylogenetics to trace transmission chains
- Core genome MLST (cgMLST) for high-resolution typing
- Example: Tracking *S. aureus* MRSA outbreaks in hospital wards

#### Antimicrobial Resistance (AMR) Profiling
- Detect known resistance genes (ABRicate, AMRFinderPlus)
- Identify chromosomal point mutations (e.g., *gyrA* in fluoroquinolone resistance)

#### Pangenome Analysis
- Compare gene content across hundreds to thousands of isolates
- Core vs. accessory genome (Roary, Panaroo)
- Allele-level variation (WhatsGNU)

#### Shotgun Metagenomics
- Profile entire microbial communities from clinical or environmental samples
- Taxonomic composition + functional potential
- Identify AMR genes directly from samples without culture

### Limitations of Short Reads
- **Cannot resolve repeats** longer than the read length (~300 bp)
  - IS elements (700–2,000 bp) — very common in bacteria
  - rRNA operons (~5,000 bp) — most bacteria have 1–15 copies
  - Transposons (2,000–40,000 bp)
- **Fragmented assemblies**: Typical bacterial assembly = 30–200 contigs
- **Cannot reliably close genomes**: You get a draft, not a complete chromosome
- **Mobile elements**: Cannot determine if a resistance gene is on a plasmid or chromosome
- **Phase variation / methylation**: Invisible to standard Illumina

---

## 3. Long-Read Sequencing (Third Generation)

### Oxford Nanopore Technologies (ONT)

#### How It Works
- Single-stranded DNA passes through a protein nanopore
- Changes in electrical current as bases transit → base calling
- Real-time sequencing — data streams as the run progresses

#### Key Platforms

| Platform | Output | Best For |
|----------|--------|----------|
| Flongle | ~2 Gb | Single isolate, rapid outbreak response |
| MinION | ~50 Gb | Field deployable, 1–10 bacterial genomes |
| PromethION | ~300 Gb | Large-scale projects, metagenomics |

#### Strengths for Microbiology
- **Ultra-long reads** (records > 4 Mb!) — span entire operons, IS elements, phage regions
- **Portable**: MinION runs off a laptop — used in field settings across Africa
- **Real-time**: Start analyzing data during the run
- **Native methylation detection**: See epigenetic modifications without bisulfite treatment
- **Rapid library prep**: Some protocols < 10 minutes

### PacBio (Pacific Biosciences)

#### How It Works
- Single-molecule real-time (SMRT) sequencing
- Polymerase anchored in a zero-mode waveguide (ZMW)
- Circular consensus sequencing (CCS) → HiFi reads (Q30+, ~10–25 kb)

#### Key Platforms

| Platform | Output | Best For |
|----------|--------|----------|
| Sequel IIe | ~30 Gb HiFi | High-accuracy long-read WGS |
| Revio | ~90 Gb HiFi | Large-scale, high-accuracy projects |

#### Strengths for Microbiology
- **HiFi reads**: Long AND accurate — best of both worlds
- **Complete genomes**: Routinely close bacterial chromosomes + plasmids
- **Methylation**: Detects base modifications (m6A, m4C, m5C)

### Use Cases for Long Reads in Bacterial Genomics

#### Complete Genome Assembly
- Close chromosomes and plasmids into single circular contigs
- Resolve all copies of rRNA operons, IS elements, transposons
- Essential for reference genome construction

#### Plasmid Characterization
- Determine if AMR genes are chromosomal or plasmid-borne
- Reconstruct complete plasmid sequences including transfer regions
- Track plasmid transmission between species

#### Phage & Mobile Genetic Elements
- Identify intact prophages integrated in chromosomes
- Characterize pathogenicity islands, integrative conjugative elements (ICEs)
- Map insertion sites precisely

#### Methylation & Epigenetics
- Detect restriction-modification (R-M) systems
- Understand phase variation mechanisms
- Identify methyltransferase specificities

#### Real-Time Outbreak Response
- ONT MinION deployed in field: Ebola (West Africa), Zika, COVID-19
- Bacterial meningitis surveillance in sub-Saharan Africa
- Results within hours of sample collection

---

## Hybrid Assembly: The Best of Both Worlds

Combining short reads (accuracy) + long reads (contiguity):

### Approach
1. Generate Illumina short reads (~100× coverage)
2. Generate ONT or PacBio long reads (~30–50× coverage)
3. Hybrid assembly: Unicycler, Trycycler, or Dragonflye

### Result
- Complete, closed chromosomes and plasmids
- High base-level accuracy (polished by short reads)
- Resolved repeats (scaffolded by long reads)

### When to Use
- Reference genome construction for your organism of interest
- When plasmid context matters (AMR, virulence)
- When you need to characterize mobile elements precisely

---

## Choosing the Right Technology: A Decision Guide

| Your Question | Recommended Approach |
|--------------|---------------------|
| "Is this *S. aureus* MRSA?" | Sanger (PCR + sequence *mecA*) or Illumina WGS |
| "How are these 50 outbreak isolates related?" | Illumina WGS → SNP phylogeny |
| "What resistance genes are in this isolate?" | Illumina WGS → ABRicate / AMRFinderPlus |
| "Is *bla*NDM on a plasmid or chromosome?" | Long-read (ONT/PacBio) or hybrid assembly |
| "What's the complete genome of our reference strain?" | Hybrid (Illumina + ONT/PacBio) |
| "What bacteria are in this clinical sample?" | Illumina shotgun metagenomics |
| "I need results in 6 hours during an outbreak" | ONT MinION + rapid library prep |
| "What's the pangenome of 1,000 isolates?" | Illumina WGS → Roary/Panaroo/WhatsGNU |
| "What methylation patterns does this strain have?" | ONT or PacBio (native modification detection) |

---

## The African Context: Practical Considerations

### Infrastructure Realities
- **Power stability**: ONT MinION is battery-friendly; Illumina instruments need stable power and UPS
- **Internet**: Large Illumina datasets (hundreds of GB) need bandwidth for upload; ONT adaptive sampling can reduce data needs
- **Cold chain**: Some library prep reagents need −20°C storage
- **Compute**: Assembly and analysis can run on modest laptops (especially for single genomes)

### What's Working Well
- MinION deployments for real-time surveillance across multiple African countries
- Illumina MiSeq/iSeq installations growing at national reference labs
- Cloud computing (Galaxy, Terra) reducing local compute requirements
- AllTheBacteria providing pre-assembled context for ~2.4M genomes

### Cost-Effectiveness
- Hackflex library prep: ~$1–2 per library vs. ~$15–20 standard Illumina DNA Prep
- ONT Flongle: ~$90 per flow cell — can sequence 1–2 bacterial genomes
- Pooling/multiplexing: 96 bacterial genomes on a single MiSeq run

---

## Where Is Sequencing Going?

- **Accuracy convergence**: ONT raw accuracy approaching Q20+ (99%); duplex reads reaching Q30
- **Speed**: ONT rapid kits: sample to sequence in < 2 hours
- **Cost**: Continuing to drop — bacterial WGS approaching the cost of a PCR panel
- **Integration with AI**: Automated base calling, assembly, and interpretation
- **Portable diagnostics**: Sequencing at point of care, not just in central labs
- **Adaptive sequencing**: ONT can selectively sequence target regions in real time

---

## Key Takeaways

1. **There is no single "best" technology** — it depends on your question
2. **Illumina is the workhorse** for routine bacterial WGS and surveillance
3. **Long reads solve problems short reads cannot** — repeats, plasmids, methylation
4. **Hybrid assembly gives you the most complete picture** when resources allow
5. **ONT is transformative for resource-limited and field settings**
6. **Cost is no longer the barrier it once was** — the barrier is training, and that's why you're here

---

## Further Readings

- Loman NJ & Pallen MJ (2015). Twenty years of bacterial genome sequencing. *Nature Reviews Microbiology*.
- Wick RR et al. (2023). Benchmarking of long-read assemblers for prokaryote whole genome sequencing. *F1000Research*.
- AllTheBacteria resource — [allthebacteria.org](https://allthebacteria.org)
- Quick J et al. (2016). Real-time, portable genome sequencing for Ebola surveillance. *Nature*.
- Hackflex protocol — [dx.doi.org/10.1186/s12864-019-6419-1](https://dx.doi.org/10.1186/s12864-019-6419-1)

---

*"A genome without context is just letters. Sequencing gives you the letters — bioinformatics gives you the story."*
