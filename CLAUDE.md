# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Repository Overview

This is an Obsidian knowledge vault containing academic notes, project documentation, and research materials. The repository is structured as a personal knowledge management system with markdown files organized across several key directories.

## Personal Mission Statement

**Core Focus**: Bridge the gap between what we want to compute and what hardware can actually deliver at scale.

I'm drawn to humanity's most computationally intensive challenges - problems where the limiting factor isn't conceptual understanding, but our ability to execute massive parallel computations efficiently. My expertise lies in compiler optimization and parallel execution architectures, transforming complex computational problems into efficient execution across distributed systems.

**Why Compilers Matter**:
- **Leverage multiplier**: Every optimization gets applied millions of times
- **Cross-domain impact**: The same scheduling/parallelization techniques work across vastly different fields
- **Foundational role**: Building the tools that enable breakthroughs in other domains
- **Future-proofing**: As hardware evolves (quantum, neuromorphic, photonic), someone needs to make it programmable

**Relevant Domains**: Scientific computing, machine learning, graphics, computational biology, financial computing, autonomous systems, climate modeling, cryptography, and robotics - all united by the need for efficient parallel computation at scale.

## Repository Structure

- **Wiki/**: Core knowledge base with technical articles, philosophy notes, and concept explanations (~180 files)
- **Projects/**: Documentation for personal technical projects including emulators, rendering systems, and research work
- **References/**: Academic papers and research citations in markdown format
- **Daily/**: Personal daily notes (excluded from git via .gitignore)
- **Resources/**: Supporting materials and assets
- **Templates/**: Obsidian templates for note creation
- **Ideas/**: Brainstorming and conceptual notes
- **Control Nodes/**: Organizational structure files for the knowledge graph
- **Workbenches/**: Canvas files for visual thinking and mind mapping

## Working with This Repository

### File Organization
- All content files use markdown (.md) format
- Files are interconnected using Obsidian's wikilink syntax `[[filename]]`
- The vault uses a flat structure within each directory for easy linking
- No build process or compilation steps are required

### Obsidian Integration
- This repository is designed to work with Obsidian.md
- Configuration stored in `.obsidian/` directory (excluded from git)
- Uses various Obsidian plugins for enhanced functionality
- Daily notes are automatically generated but kept private

### Content Guidelines
- Technical notes often include code snippets and architectural diagrams
- Academic references follow a consistent citation format
- Project documentation includes implementation details and learnings
- Philosophy and research notes connect concepts across disciplines

### Git Workflow
- Daily notes are excluded via .gitignore to maintain privacy
- Obsidian workspace files are excluded to prevent conflicts
- Standard markdown files are tracked and versioned
- Repository uses descriptive commit messages for vault backups