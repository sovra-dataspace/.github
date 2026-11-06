<a id="readme-top"></a>

<!--
  Organization profile shown at https://github.com/sovra-dataspace.
  Based on Best-README-Template. Spanish version: README.es.md. Keep both in sync.
-->

**English** · [Español](README.es.md)

[![DSP TCK][tck-shield]][tck-url]
[![DCP TCK][dcp-tck-shield]][dcp-tck-url]
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
    <a href="https://github.com/sovra-dataspace/desktop">Desktop</a>
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

**Sovra builds data space infrastructure.** Its core is `dataspace-core`, a connector written in Rust that every participant runs to take part in a data space: on a server (a signed Docker image and a Helm chart, for any platform) or, for a person or a small organization, in the **Sovra desktop application** for Windows and Linux.

The name comes from **sovereignty**: *data sovereignty*, the core idea of data spaces. Each organization keeps control over its data: who may use it, for what and under which conditions. Sovra makes that sovereignty real with the three open standards of data spaces, which we implement strictly and verify with their official test suites (TCK, *Technology Compatibility Kit*):

| Standard | What it solves | Status |
|---|---|---|
| **Eclipse Dataspace Protocol (DSP)** | How connectors publish catalogs, negotiate contracts and transfer data | ✅ Official TCK 65/65 |
| **Decentralized Claims Protocol (DCP)** | How connectors prove who they are with verifiable credentials | ✅ Official TCK 117/117 |
| **OpenID4VCI / OpenID4VP** | How credentials are issued and presented | ✅ OpenID Foundation conformance suite: verifier 14/14, issuer 20/20 |

What we add around the standards, without changing them:

- **One binary + SQLite**: a connector that any organization can deploy.
- **Mandatory, auditable connector**: every transaction goes through a connector that records it.
- **Simple access for people**: username and password. Official certificates and existing identity wallets through an optional module, never a requirement.
- **Web console in the connector itself**: first-start wizard, users with roles and an optional second factor, network topology and audit trail ([console](https://github.com/sovra-dataspace/dataspace-core/blob/main/docs/console.md)).
- **Zero-trust network**: mutual TLS between connectors, a signed directory and a relay for connectors behind NAT, with no public IP needed ([zero-trust network](https://github.com/sovra-dataspace/dataspace-core/blob/main/docs/zero-trust-network.md)).
- **Several data spaces per connector**: member of several spaces, or authority of some, with a separate identity, credentials, catalog, agreements and audit trail in each ([spaces](https://github.com/sovra-dataspace/dataspace-core/blob/main/docs/spaces.md)).
- **No single point of failure**: the authority can be shared among several authority nodes, each with every function (relay included) and its own keys; decisions such as admitting or revoking a connector are approved by a majority of them, like a pull request, and the space keeps working while one is down ([decentralized authority](https://github.com/sovra-dataspace/dataspace-core/blob/main/docs/decentralized-authority.md)).
- **The owner decides, after talking**: each request for your data waits for you to accept or reject it; meanwhile both parties write, propose conditions of use, send documents and sign them in a **negotiation room**, signed with each connector's key, recorded in the audit trail of both and linked to the agreement ([negotiation room](https://github.com/sovra-dataspace/dataspace-core/blob/main/docs/negotiation-room.md)).
- **One catalog for the whole space**: everything every member publishes, with its owner, built by each connector without a central index.
- **Deploy anywhere**: every version is published as a signed image (`ghcr.io/sovra-dataspace/sovra`) and a Helm chart; ready files for any server with Docker or any Kubernetes, and a guide to put an authority on the internet ([public authority](https://github.com/sovra-dataspace/dataspace-core/blob/main/docs/public-authority.md), [releases](https://github.com/sovra-dataspace/dataspace-core/blob/main/docs/releases.md)).
- **One connector, every platform**: the desktop application runs the same connector, as a member of data spaces (never their authority, which is a server), with nothing to open on the router.
- **Lightweight and extensible**: the minimum connector ships only what secure data exchange needs; everything else is a signed module installed from the dashboard.

<p align="right">(<a href="#readme-top">back to top</a>)</p>

## What is a data space?

A **data space** is an environment where organizations share data and APIs under agreed rules **without losing control**: each provider decides who may use its data, for what and under which conditions, and every exchange is backed by a contract negotiated between the parties' connectors. Examples are the European common data spaces for health, mobility, energy or agriculture.

<p align="right">(<a href="#readme-top">back to top</a>)</p>

## Repositories

> 🔒 The repositories are **private during early development** and will be opened once the first milestones are consolidated. The links below only work for organization members for now.

| Repository | Purpose |
|---|---|
| [`dataspace-core`](https://github.com/sovra-dataspace/dataspace-core) | The data space connector in Rust: core + modules (DSP, DCP, OpenID4VC) |
| [`desktop`](https://github.com/sovra-dataspace/desktop) | The desktop application (Windows, Linux): the same connector, as a member |
| [`platform`](https://github.com/sovra-dataspace/platform) | Roadmap, overall architecture, decisions and conventions |
| [`.github`](https://github.com/sovra-dataspace/.github) | This profile and the VS Code workspace for all repositories |
| ~~`consola-web`~~ *(dropped)* | The web console is served by the connector itself, in `dataspace-core` |
| `despliegue` *(planned)* | Multi-participant pilot environment |

<p align="right">(<a href="#readme-top">back to top</a>)</p>

## Getting Started

**To use Sovra**: install the desktop application from the [releases of `desktop`](https://github.com/sovra-dataspace/desktop/releases), or run a connector on a server with the image or the chart of a [release of `dataspace-core`](https://github.com/sovra-dataspace/dataspace-core/releases) ([guide](https://github.com/sovra-dataspace/dataspace-core/blob/main/docs/public-authority.md)).

**To develop** you need **Docker** and **VS Code** with the *Dev Containers* extension.

1. Clone the repositories side by side:
   ```sh
   git clone https://github.com/sovra-dataspace/.github
   git clone https://github.com/sovra-dataspace/platform
   git clone https://github.com/sovra-dataspace/dataspace-core
   git clone https://github.com/sovra-dataspace/desktop
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
[dcp-tck-shield]: https://img.shields.io/badge/DCP_TCK-117%2F117-brightgreen?style=for-the-badge
[dcp-tck-url]: https://github.com/sovra-dataspace/dataspace-core/blob/main/docs/dcp.md#conformance-the-official-dcp-tck
[license-shield]: https://img.shields.io/badge/license-Apache--2.0-blue?style=for-the-badge
[license-url]: https://github.com/sovra-dataspace/dataspace-core/blob/main/LICENSE
