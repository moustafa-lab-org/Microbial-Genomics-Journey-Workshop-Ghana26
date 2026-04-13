# No Code? No Problem.
## From Point-and-Click to Vibe Coding Your Own Tools

**Microbial Genomics Journey Workshop – Ghana 2026**
**Instructor: Ahmed M. Moustafa**

---

## The Bioinformatics Spectrum

Bioinformatics is not a switch you flip — it is a spectrum. Every expert you admire started exactly where you are right now.

| Level | What It Looks Like | Example |
|-------|-------------------|---------|
| 🖱️ Point-and-Click | Using web interfaces | NCBI BLAST, Galaxy, BV-BRC |
| ⌨️ Command Line | Running tools others built | `shovill`, `mlst`, `snippy` |
| 📝 Scripting | Writing your own glue code | Bash loops, Python scripts |
| 🔧 Tool Building | Creating tools others use | WhatsGNU, Cladebreaker, Roary |
| 🤖 Vibe Coding | Describing what you want and AI builds it | Claude, Cursor, GitHub Copilot |

**You do not need to be a computer geek to move along this spectrum.**

---

## My Journey (Yes, I Was Not a "Computer Person")

- Started as a microbiologist who just wanted answers about bacteria
- First bioinformatics: uploading a FASTA to NCBI BLAST and waiting
- Learned Unix because I *had* to, not because I *wanted* to
- Wrote my first script because copy-pasting 200 commands was painful
- Built WhatsGNU because no tool did what I needed
- Today: building AI agents that chain entire genomics workflows

**The secret?** I never decided to "become a bioinformatician." I just kept solving the next problem in front of me.

---

## The Old Path vs. The New Path

### The Old Path (Still Valid!)
1. Learn Unix basics
2. Learn a scripting language (Python, R, Perl)
3. Understand data formats (FASTA, FASTQ, VCF, GFF)
4. Run existing tools
5. String tools into pipelines
6. Eventually build your own tools
7. **Timeline: months to years**

### The New Path (Vibe Coding Era)
1. Understand your biological question
2. Know what data formats look like
3. Describe what you want in plain English
4. AI writes the code, you guide the direction
5. Iterate: "No, I meant filter by coverage > 30"
6. You have a working tool
7. **Timeline: hours to days**
8. **Be careful as you will get answers, but is it the right one?**

**The old path teaches you foundations. The new path gives you superpowers. The best approach? Both.**

---

## What Is Vibe Coding?

Coined by Andrej Karpathy (2025):

> *"You fully give in to the vibes, embrace exponentials, and forget that the code even exists."*

In practice, vibe coding means:

- You describe what you want in natural language
- An AI model (Claude, GPT, Copilot) writes the code
- You test it, tweak your description, iterate
- You don't need to understand every line — you need to understand the **biology** and the **logic**

### Vibe Coding for Microbial Genomics
- "Write a script that takes a folder of assemblies, runs Prokka on each, and summarizes the number of CDS per genome in a table"
- "Build me a Snakemake pipeline that goes from raw reads to a SNP phylogeny"
- "Create a visualization comparing pangenome size across 50 *S. aureus* genomes"

**The biological knowledge in your head is what makes the code useful. AI cannot replace that.**

---

## The Golden Age: Why NOW Is the Best Time

### For You, Right Here, Right Now

- **Free tools everywhere**: Galaxy, BV-BRC, NCBI, EBI — no installation needed to start
- **Command-line tools are mature**: Shovill, Bakta, Snippy, Roary — well-documented, community-supported
- **AI coding assistants**: Claude, GitHub Copilot, Cursor — write code in English
- **Massive public databases**: AllTheBacteria (~2.7M genomes), NCBI SRA, ENA
- **Community**: workshops like this one, Twitter/X, GitHub, Slack groups

### What Took Months Now Takes Hours

| Task | 2015 | 2025+ |
|------|------|-------|
| Annotate a genome | Learn Perl, install Prokka manually, debug dependencies | `conda install prokka` or ask AI |
| Build a phylogeny | Write custom scripts, format conversion headaches | `snippy` → `iqtree` pipeline in one afternoon |
| Create a custom tool | Months of learning, testing, packaging | Describe it to Claude, test, iterate, publish |

---

## Real Examples: Vibe Coding in Action

### Example 1: From Question to Script in 5 Minutes
**Question:** "Which of my 30 assemblies have the *mecA* gene?"

**Prompt to AI:**
*"Write a Python script that takes a folder of genome FASTA files and BLASTs each against a reference mecA sequence. Output a table showing filename, percent identity, and coverage."*

→ Working script, first try. Debug with: *"It crashes on empty BLAST results — add error handling."*

### Example 2: Building an Interactive Dashboard
**Question:** "I want to visualize MLST distribution across my isolates"

**Prompt to AI:**
*"Create an interactive HTML dashboard that reads a TSV of sample names, MLST types, and collection dates. Show a bar chart of ST frequencies and a timeline."*

→ Shareable HTML file, no web development experience needed.

### Example 3: An Entire AI Agent for Genomics
**Question:** "Can I automate the full pipeline from reads to epidemiological context?"

→ This is exactly what the atb-ai-agent does: reads → assembly → annotation → MLST → AllTheBacteria context → literature search — all chained by an AI agent that decides the next step.

---

## The Mindset Shift

### Stop Thinking:
- ❌ "I'm not technical enough"
- ❌ "I need to learn Python first before I can do anything"
- ❌ "Bioinformatics is for computer scientists"
- ❌ "I'll never be as good as people who've coded since childhood"

### Start Thinking:
- ✅ "I understand the biology — that's my superpower"
- ✅ "I can describe what I need and iterate"
- ✅ "Every tool I learn is a permanent addition to my toolkit"
- ✅ "Similar to learning skills on the bench (e.g. PCR, Gel electrophoresis), I can learn bioinformatics"

---

## Your Journey This Week

By the end of this workshop, you will have moved along the spectrum:

- 📁 You will be comfortable in the terminal
- 🧬 You will go from raw reads to an annotated, typed genome
- 🌳 You will build phylogenies and pangenomes


---

## Further Resources

- **AllTheBacteria**: ~2.7 million pre-assembled bacterial genomes — [allthebacteria.org](https://allthebacteria.org)
- **Galaxy Project**: Free, web-based bioinformatics — [usegalaxy.org](https://usegalaxy.org)
- **BV-BRC**: Bacterial & Viral Bioinformatics Resource Center — [bv-brc.org](https://www.bv-brc.org)
- **Claude AI**: [claude.ai](https://claude.ai) — your vibe coding partner

---

*"The journey of a thousand genomes begins with a single BLAST."*
