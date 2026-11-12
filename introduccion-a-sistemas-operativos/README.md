# Introduction to Operating Systems — Interactive Laboratories (IaSO · UNLa)

Interactive, self-contained web laboratories developed for the **Introduction to Operating Systems (*Introducción a los Sistemas Operativos*)** course in the **Bachelor's Degree in Systems (*Licenciatura en Sistemas*)** at the **National University of Lanús (*Universidad Nacional de Lanús — UNLa*)**.

The entire suite is packaged into a single, zero-dependency HTML file (`laboratorios-iaso.html`) that runs directly in any modern web browser without requiring a build step, external server, or runtime installation.

---

## Quick Start

1. Clone or download this repository.
2. Open `laboratorios-iaso.html` directly in any modern browser (Chrome, Firefox, Safari, Edge).
3. Use the top navigation bar to switch between **Unit 5a**, **Unit 5b**, and **Unit 6**.

---

## Laboratory Modules

### 1. Unit 5a · Memory Management (`Unidad 5a · Administración de Memoria`)

Explores the three core goals of main memory management—**abstraction**, **optimization**, and **protection & sharing**—through step-by-step hardware/OS visual simulations:

- **Objectives Overview (`Objetivos`)**: Summary of memory management goals and a comparative matrix of contiguous vs. non-contiguous allocation schemes.
- **1 · Process Image (`Imagen del proceso`)**: Visualizes how a process perceives its own logical address space (`0..X B`) independently of where it resides in physical RAM (`0..N B`).
- **2 · Relative Address & Dynamic Relocation (`Dirección relativa y reubicación`)**: Simulates hardware address translation using the **Base** and **Limit** registers stored in the Process Control Block (PCB), including out-of-bounds trap detection.
- **3 · Dynamic Partitioning (`Partición dinámica`)**: Simulates variable-size contiguous allocation across an arrival/departure process queue. Compares **First Fit**, **Best Fit**, **Worst Fit**, and **Next Fit** placement algorithms, highlights **external fragmentation**, and demonstrates memory **compaction**.
- **4 · Fixed Partitioning (`Partición fija`)**: Models equal-size and variable-size static partitions, placement strategies (first available vs. best-fitting partition), and **internal fragmentation**.
- **5 · Paging (`Paginación`)**: Demonstrates non-contiguous allocation (`Page = Frame`), per-process Page Tables managed by the OS, and logical-to-physical address translation (page number + offset and binary bit splitting) performed by hardware.
- **6 · Segmentation + Paging (`Segmentación + Paginación`)**: Combines logical segments with paging, illustrating Segment Tables, Page Tables, per-segment protection attributes (`R`/`W`/`X`), and shared segments between processes.

---

### 2. Unit 5b · Virtual Memory Management (`Unidad 5b · Administración de Memoria Virtual`)

Covers partial process loading, hardware/OS page fault handling, locality of reference, and page replacement policies:

- **1 · Virtual Memory Concept (`Idea de memoria virtual`)**: Compares execution with and without virtual memory across a limited number of physical RAM frames backed by secondary storage.
- **2 · Paging With & Without Virtual Memory (`Paginación sin y con memoria virtual`)**: Contrasts full-process loading against resident sets where non-resident pages remain on disk.
- **3 · Address Translation with Present Bit (`Traducción de direcciones con bit de presencia`)**: Animates the complete MMU and OS trap workflow when translating relative addresses—handling hits (`P = 1`) as well as page faults (`P = 0`), disk I/O reads, page table updates, and instruction restarts.
- **4 · Principle of Locality & Working Set (`Principio de vecindad y conjunto de trabajo`)**: Visualizes temporal and spatial locality over memory reference traces and computes the Working Set window $W(t, \Delta)$.
- **5 · Virtual Memory Policies (`Políticas de manejo de la memoria virtual`)**: Interactive comparisons of:
  - **Fetch Policy**: Demand paging vs. Prepaging.
  - **Cleaning Policy**: Demand cleaning vs. Precleaning.
  - **Replacement Scope & Allocation**: Local vs. Global replacement, Fixed vs. Variable frame allocation.
- **6 · Page Replacement Algorithms (`Algoritmos de reemplazo`)**: Simulates **Optimal (OPT)**, **FIFO**, **LRU**, **LFU**, and **Clock / Second Chance** algorithms. Includes the official course table view, classic grid view, side-by-side algorithm comparison, custom reference string configuration, and an interactive demonstration of **Belady's Anomaly**.

---

### 3. Unit 6 · File System Management (`Unidad 6 · Administración de Sistemas de Archivos`)

Traces file storage from high-level user paths and permissions down to logical block allocation and physical disk geometry:

- **1 · File System Layers (`Capas`)**: End-to-end walkthrough of a file read request (`pepe.txt`) traversing the Application, File Layer, Logical Organization Layer, and Physical Organization Layer down to the disk controller.
- **2 · Directory Tree & File Table (`Árbol de directorios y Tabla de Archivos`)**: Interactive **Linux** and **Windows** directory hierarchies, step-by-step path resolution (including symbolic links/shortcuts), file lifecycle operations (`create`, `open`, `read`, `write`, `close`, `delete`), internal fragmentation calculation, and UNIX permission checks (`rwx`).
- **3 · Logical Organization & Disk Allocation (`Archivo de datos → Disco Lógico`)**: Simulates **Contiguous**, **Chained (Linked)**, and **Indexed** allocation on an 80-cluster logical disk. Compares disk read counts for sequential and direct block access, demonstrates external fragmentation and compaction, simulates cluster damage/corruption impact, and visualizes **Free Space Management** (**Bitmaps**, **Linked Free Lists**, and **Hole Lists**).
- **4 · Inodes & Multi-Level Indirection (`INodo: punteros directos e indirecciones`)**: Interactive pointer-path visualizer and maximum file size calculator for Direct Pointers, Single, Double, and Triple Indirection:
  $$\text{Max Size} = (D + n + n^2 + n^3) \times \text{Block Size}, \quad n = \left\lfloor \frac{\text{Block Size}}{\text{Pointer Size}} \right\rfloor$$
- **5 · Physical Organization (`Disco Lógico → Disco Físico`)**: Maps logical clusters to Logical Block Addresses (LBA), tracks, and physical sectors on an animated rotating disk platter. Illustrates **seek time** (actuator arm movement), **rotational latency**, and **transfer time**, plus a head-movement cost analyzer comparing contiguous vs. scattered cluster sequences.

---

## Interactive & Pedagogical Features

- **Step-by-Step Playback**: Every simulation includes a step controller with detailed explanations of what happens at each micro-step.
- **Side Panel Learning Aids**:
  - **Step-by-Step (`Paso a paso`)**: Clickable timeline of the active simulation trace.
  - **Pros & Cons (`Ventajas y desventajas`)**: Structured trade-off analysis for each technique.
  - **Practice Exercises (`Ejercicio`)**: Randomized problem generator with instant validation and worked step-by-step solutions.
- **Projector Mode (`Modo Proyector`)**: High-contrast, large-font layout optimized for classroom lectures and projection (`P` key).
- **Audio Feedback (`Sonido`)**: Optional synthesized Web Audio cues for steps, hits, and faults (`S` key, muted by default).
- **SVG Diagram Export**: One-click SVG source export on diagrams for inclusion in lecture notes or study guides.
- **Built-In Self-Verification (`runSelfTests`)**: Automated test suites run on startup for every unit to verify algorithm accuracy against the official course examples.

---

## Keyboard Shortcuts

| Key | Action |
| :--- | :--- |
| <kbd>←</kbd> / <kbd>→</kbd> | Previous / Next simulation step |
| <kbd>Space</kbd> | Play / Pause automatic step progression |
| <kbd>R</kbd> | Reset current simulation to step 1 |
| <kbd>P</kbd> | Toggle classroom **Projector Mode** |
| <kbd>S</kbd> | Toggle **Sound** effects on/off |

---

## Technical Architecture

- **Single-File Bundle (`laboratorios-iaso.html`)**: Uses HTML `<template>` elements and an isolated Shadow DOM top bar (`window.IASO`) to mount one unit at a time, cleanly scoping CSS stylesheets, DOM nodes, timers, and keyboard listeners per unit while saving state in `sessionStorage`.
- **Accessible Vector Graphics**: All diagrams are dynamically rendered as scalable inline SVGs with distinct hatching patterns and semantic colors so visual distinctions never rely on color alone.

---

## Academic References

- **Course Material**: *Introducción a los Sistemas Operativos* — Licenciatura en Sistemas, Universidad Nacional de Lanús (UNLa), Study Guides No. 5 & No. 6.
- **Stallings, W.** (2011). *Operating Systems: Internals and Design Principles* (7th ed.). Prentice Hall — Chapters 7, 8, and 12.
- **Tanenbaum, A. S.** (2009). *Modern Operating Systems* (3rd ed.). Prentice Hall — Chapters 3 and 4.
