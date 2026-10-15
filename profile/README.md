<a id="readme-top"></a>

<!--
  Organization profile shown at https://github.com/sovra-dataspace.
  Based on Best-README-Template. Spanish version: README.es.md. Keep both in sync.
-->

**English** · [Español](README.es.md)

[![DSP TCK][tck-shield]][tck-url]
[![License][license-shield]][license-url]

<br />
<div align="center">
  <h3 align="center">Sovra · Data Spaces</h3>

  <p align="center">
    Open-source <strong>data space</strong> software: connectors through which organizations share data and APIs under contracts, with every exchange controlled and auditable.
    <br />
    <a href="https://github.com/sovra-dataspace/platform"><strong>Read the roadmap »</strong></a>
    <br />
    <br />
    <a href="https://github.com/sovra-dataspace/dataspace-core">Connector</a>
    &middot;
    <a href="https://github.com/sovra-dataspace/platform/blob/main/docs/architecture.md">Architecture</a>
    &middot;
    <a href="https://github.com/sovra-dataspace/dataspace-core/issues">Report Bug</a>
  </p>
</div>

<details>
  <summary>Table of Contents</summary>
  <ol>
    <li><a href="#about-sovra">About Sovra</a></li>
    <li><a href="#what-is-a-data-space">What is a data space?</a></li>
    <li><a href="#repositories">Repositories</a></li>
    <li><a href="#getting-started">Getting Started</a></li>
    <li><a href="#contributing">Contributing</a></li>
    <li><a href="#license">License</a></li>
  </ol>
</details>

## About Sovra

**Sovra builds data space infrastructure.** Its core is `dataspace-core`, a connector written in Rust that every participant runs to take part in a data space.

The name comes from **sovereignty**: *data sovereignty*, the core idea of data spaces. Each organization keeps control over its data: who may use it, for what and under which conditions. Sovra makes that sovereignty real with the three open standards of data spaces, which we implement strictly and verify with their official test suites (TCK, *Technology Compatibility Kit*):

| Standard | What it solves | Status |
|---|---|---|
| **Eclipse Dataspace Protocol (DSP)** | How connectors publish catalogs, negotiate contracts and transfer data | ✅ Official TCK 65/65 |
| **Decentralized Claims Protocol (DCP)** | How connectors prove who they are with verifiable credentials | ⬜ In progress |
| **OpenID4VCI / OpenID4VP** | How credentials are issued and presented | ⬜ Planned |

What we add around the standards, without changing them:

- **One binary + SQLite**: a connector that any organization can deploy.
- **Mandatory, auditable connector**: every transaction goes through a connector that records it.
- **Simple access for people**: official certificate or username and password. An existing identity wallet is an option, never a requirement.

<p align="right">(<a href="#readme-top">back to top</a>)</p>

## What is a data space?

A **data space** is an environment where organizations share data and APIs under agreed rules **without losing control**: each provider decides who may use its data, for what and under which conditions, and every exchange is backed by a contract negotiated between the parties' connectors. Examples are the European common data spaces for health, mobility, energy or agriculture.

<p align="right">(<a href="#readme-top">back to top</a>)</p>

## Repositories

| Repository | Purpose |
|---|---|
| [`dataspace-core`](https://github.com/sovra-dataspace/dataspace-core) | The data space connector in Rust: core + modules (DSP, DCP, OpenID4VC) |
| [`platform`](https://github.com/sovra-dataspace/platform) | Roadmap, overall architecture, decisions and conventions |
| [`.github`](https://github.com/sovra-dataspace/.github) | This profile and the VS Code workspace for all repositories |
| `consola-web` *(planned)* | Connector administration and people's access portal |
| `despliegue` *(planned)* | Multi-participant pilot environment |

<p align="right">(<a href="#readme-top">back to top</a>)</p>

## Getting Started

All you need is **Docker** and **VS Code** with the *Dev Containers* extension.

1. Clone the repositories side by side:
   ```sh
   git clone https://github.com/sovra-dataspace/.github
   git clone https://github.com/sovra-dataspace/platform
   git clone https://github.com/sovra-dataspace/dataspace-core
   ```
2. Open `.github/sovra.code-workspace` in VS Code to see them all.
3. Start the connector following the [`dataspace-core` README](https://github.com/sovra-dataspace/dataspace-core#getting-started).

<p align="right">(<a href="#readme-top">back to top</a>)</p>

## Contributing

Read the [conventions](https://github.com/sovra-dataspace/platform/blob/main/docs/conventions.md) first. Code comments are always in English, and every document is written in English and Spanish.

<p align="right">(<a href="#readme-top">back to top</a>)</p>

## License

Every repository is distributed under the Apache License 2.0.

<p align="right">(<a href="#readme-top">back to top</a>)</p>

[tck-shield]: https://img.shields.io/badge/DSP_TCK-65%2F65-brightgreen?style=for-the-badge
[tck-url]: https://github.com/sovra-dataspace/dataspace-core/blob/main/docs/tck.md
[license-shield]: https://img.shields.io/badge/license-Apache--2.0-blue?style=for-the-badge
[license-url]: https://github.com/sovra-dataspace/dataspace-core/blob/main/LICENSE
