# Awesome AI Penetration Testing [![Awesome](https://awesome.re/badge.svg)](https://awesome.re)

> A curated list of AI and LLM powered penetration testing tools: autonomous platforms, interactive assistants, benchmarks, and the research behind them.

The space went from empty to crowded in about two years. This list tries to be an honest map of it: what each project actually does, whether it is open source, and how far it reaches (web only, or also Active Directory, Kubernetes and cloud). No rankings, no "this one wins". Clone the two or three that fit your constraints and test them against a lab you own.

Maintained by the team behind [Darkmoon](https://github.com/ASCIT31/Dark-Moon) (listed below, and flagged as ours). Contributions of tools we missed, including direct competitors, are very welcome. See [Contributing](#contributing).

## Contents

- [Autonomous Platforms](#autonomous-platforms)
- [LLM Assisted (Human in the Loop)](#llm-assisted-human-in-the-loop)
- [Commercial](#commercial)
- [Benchmarks and Evaluation](#benchmarks-and-evaluation)
- [Research and Reading](#research-and-reading)
- [Contributing](#contributing)

## Autonomous Platforms

Tools that take a target, reason about it with a model, and actually run offensive tooling rather than only suggesting commands.

- [Darkmoon](https://github.com/ASCIT31/Dark-Moon) - GPL-3.0 platform and MCP host with per technology sub agents. Covers web, API, Active Directory and Kubernetes; every finding carries the executed command and its output; a privacy gateway keeps real IPs, hosts and credentials away from the model. *(Full disclosure: maintained by us.)*
- [Strix](https://github.com/usestrix/strix) - Apache-2.0 autonomous agents focused on web application testing.
- [PentAGI](https://github.com/vxcontrol/pentagi) - Fully autonomous framework with an orchestrator and a memory graph, container based.
- [CAI](https://github.com/aliasrobotics/cai) - Framework for building autonomous security testing agents, with its own benchmark work.
- [HexStrike AI](https://github.com/0x4m4/hexstrike-ai) - Autonomous agent wiring an LLM to a large toolbox of offensive utilities.

## LLM Assisted (Human in the Loop)

Interactive assistants that guide a human; you stay in the loop and run the tools.

- [PentestGPT](https://github.com/GreyDGL/PentestGPT) - The project that started the wave. Interactive assistant that guides you through a pentest. Excellent for learning and CTF style work.
- [hackingBuddyGPT](https://github.com/ipa-lab/hackingBuddyGPT) - Academic, focused and honest. Good for studying how far a small model gets on privilege escalation, with published numbers.
- [HackerAI](https://hackerai.co/) - AI powered penetration testing assistant.

## Commercial

Closed source, listed for completeness because people compare against them.

- [XBOW](https://xbow.com/) - Autonomous offensive security platform; famously topped a HackerOne leaderboard.
- [NodeZero](https://www.horizon3.ai/) - Horizon3.ai autonomous pentest and validation platform.
- [Pentera](https://pentera.io/) - Automated security validation platform.

## Benchmarks and Evaluation

- [AutoPenBench](https://github.com/lucagioacchini/auto-pen-bench) - Benchmark for generative agents in automated penetration testing.
- [CVE-Bench](https://github.com/uiuc-kang-lab/cve-bench) - Benchmark for AI agents' ability to exploit real world web vulnerabilities.
- [PACEbench](https://arxiv.org/abs/2510.11688) - Framework for evaluating practical AI cyber exploitation.

## Research and Reading

- [A Survey of LLM-Driven Penetration Testing](https://arxiv.org/abs/2607.02605) - Taxonomy, co evolution and open challenges. A good first read for the whole field.
- [How to run an AI pentest without sending your data to the LLM](https://dark-moon.org/blog/ai-pentest-without-sending-data-to-the-llm/) - Design writeup on the data exposure problem (by the Darkmoon team).

## Contributing

Pull requests welcome. One entry per tool, alphabetical within a section is not required but keep descriptions factual and one line. Competitors and commercial tools are explicitly in scope; this list is more useful the more complete and neutral it is. If you maintain a tool listed here and want the description changed, open a PR.

## License

[![CC0](https://licensebuttons.net/p/zero/1.0/88x31.png)](https://creativecommons.org/publicdomain/zero/1.0/)

To the extent possible under law, the contributors have waived all copyright and related rights to this work.
