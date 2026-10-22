<a id="readme-top"></a>

<!--
  Perfil de la organización en https://github.com/sovra-dataspace.
  Basado en Best-README-Template. Versión en inglés: README.md. Mantener las dos sincronizadas.
-->

[English](README.md) · **Español**

[![DSP TCK][tck-shield]][tck-url]
[![DCP TCK][dcp-tck-shield]][dcp-tck-url]
[![Licencia][license-shield]][license-url]

<br />
<div align="center">
  <h3 align="center">Sovra · Espacios de datos</h3>

  <p align="center">
    Software libre para <strong>espacios de datos</strong>: conectores con los que las organizaciones comparten datos y APIs bajo contrato, con cada intercambio controlado y auditable.
    <br />
    <a href="https://github.com/sovra-dataspace/platform/blob/main/README.es.md"><strong>Leer la hoja de ruta »</strong></a>
    <br />
    <br />
    <a href="https://github.com/sovra-dataspace/dataspace-core/blob/main/README.es.md">Conector</a>
    &middot;
    <a href="https://github.com/sovra-dataspace/platform/blob/main/docs/architecture.es.md">Arquitectura</a>
    &middot;
    <a href="https://github.com/sovra-dataspace/dataspace-core/issues">Informar de un error</a>
  </p>
</div>

<details>
  <summary>Índice</summary>
  <ol>
    <li><a href="#acerca-de-sovra">Acerca de Sovra</a></li>
    <li><a href="#qué-es-un-espacio-de-datos">¿Qué es un espacio de datos?</a></li>
    <li><a href="#repositorios">Repositorios</a></li>
    <li><a href="#primeros-pasos">Primeros pasos</a></li>
    <li><a href="#cómo-contribuir">Cómo contribuir</a></li>
    <li><a href="#licencia">Licencia</a></li>
  </ol>
</details>

## Acerca de Sovra

**Sovra construye infraestructura para espacios de datos.** Su pieza central es `dataspace-core`, un conector escrito en Rust que ejecuta cada participante para formar parte de un espacio de datos.

El nombre viene de **soberanía**: la *soberanía del dato*, la idea central de los espacios de datos. Cada organización conserva el control sobre sus datos: quién puede usarlos, para qué y en qué condiciones. Sovra hace real esa soberanía con los tres estándares abiertos de los espacios de datos, que implementamos de forma estricta y verificamos con sus baterías de pruebas oficiales (TCK, *Technology Compatibility Kit*):

| Estándar | Qué resuelve | Estado |
|---|---|---|
| **Eclipse Dataspace Protocol (DSP)** | Cómo los conectores publican catálogos, negocian contratos y transfieren datos | ✅ TCK oficial 65/65 |
| **Decentralized Claims Protocol (DCP)** | Cómo los conectores demuestran quiénes son con credenciales verificables | ✅ TCK oficial 117/117 |
| **OpenID4VCI / OpenID4VP** | Cómo se emiten y presentan las credenciales | ⬜ Previsto |

Lo que añadimos alrededor de los estándares, sin modificarlos:

- **Un binario + SQLite**: un conector que cualquier organización puede desplegar.
- **Conector obligatorio y auditable**: toda transacción pasa por un conector que la registra.
- **Acceso sencillo para las personas**: usuario y contraseña. Certificados oficiales y carteras de identidad existentes con un módulo opcional, nunca como requisito.
- **Consola web en el propio conector**: asistente de primer arranque, usuarios con roles y segundo factor opcional, topología de la red y auditoría ([consola](https://github.com/sovra-dataspace/dataspace-core/blob/main/docs/console.es.md)).
- **Red de confianza cero**: TLS mutuo entre conectores, directorio firmado y relé para los conectores detrás de NAT, sin necesidad de IP pública ([red de confianza cero](https://github.com/sovra-dataspace/dataspace-core/blob/main/docs/zero-trust-network.es.md)).
- **Varios espacios de datos por conector**: miembro de varios espacios, o autoridad de alguno, con identidad, credenciales, catálogo, acuerdos y auditoría separados en cada uno ([espacios](https://github.com/sovra-dataspace/dataspace-core/blob/main/docs/spaces.es.md)).
- **Sin punto único de fallo**: los miembros que acredita la autoridad replican lo que ella publica, todo firmado por ella, para que el espacio siga funcionando aunque la autoridad caiga ([réplicas](https://github.com/sovra-dataspace/dataspace-core/blob/main/docs/replicas.es.md)).
- **Ligero y ampliable**: el conector mínimo trae solo lo que necesita el intercambio seguro de datos; el resto son módulos firmados que se instalan desde el panel.

<p align="right">(<a href="#readme-top">volver arriba</a>)</p>

## ¿Qué es un espacio de datos?

Un **espacio de datos** es un entorno en el que organizaciones comparten datos y APIs bajo reglas acordadas **sin perder el control**: cada proveedor decide quién puede usar sus datos, para qué y en qué condiciones, y cada intercambio se apoya en un contrato negociado entre los conectores de las partes. Ejemplos son los espacios comunes de datos europeos de salud, movilidad, energía o agricultura.

<p align="right">(<a href="#readme-top">volver arriba</a>)</p>

## Repositorios

> 🔒 Los repositorios son **privados durante las primeras fases de desarrollo** y se abrirán cuando se consoliden los primeros hitos. Por ahora, los enlaces de abajo solo funcionan para los miembros de la organización.

| Repo | Para qué |
|---|---|
| [`dataspace-core`](https://github.com/sovra-dataspace/dataspace-core/blob/main/README.es.md) | El conector de espacios de datos en Rust: núcleo + módulos (DSP, DCP, OpenID4VC) |
| [`platform`](https://github.com/sovra-dataspace/platform/blob/main/README.es.md) | Hoja de ruta, arquitectura global, decisiones y convenciones |
| [`.github`](https://github.com/sovra-dataspace/.github) | Este perfil y el workspace de VS Code con todos los repos |
| ~~`consola-web`~~ *(descartado)* | La consola web la sirve el propio conector, en `dataspace-core` |
| `despliegue` *(previsto)* | Entorno del piloto con varios participantes |

<p align="right">(<a href="#readme-top">volver arriba</a>)</p>

## Primeros pasos

Solo hacen falta **Docker** y **VS Code** con la extensión *Dev Containers*.

1. Clona los repos uno al lado del otro:
   ```sh
   git clone https://github.com/sovra-dataspace/.github
   git clone https://github.com/sovra-dataspace/platform
   git clone https://github.com/sovra-dataspace/dataspace-core
   ```
2. Abre `.github/sovra.code-workspace` en VS Code para verlos todos.
3. Arranca el conector siguiendo el [README de `dataspace-core`](https://github.com/sovra-dataspace/dataspace-core/blob/main/README.es.md#primeros-pasos).

<p align="right">(<a href="#readme-top">volver arriba</a>)</p>

## Cómo contribuir

Lee primero las [convenciones](https://github.com/sovra-dataspace/platform/blob/main/docs/conventions.es.md). Los comentarios del código van siempre en inglés, y todo documento se escribe en inglés y en español.

<p align="right">(<a href="#readme-top">volver arriba</a>)</p>

## Licencia

Todos los repos se distribuyen bajo la Licencia Apache 2.0.

<p align="right">(<a href="#readme-top">volver arriba</a>)</p>

[tck-shield]: https://img.shields.io/badge/DSP_TCK-65%2F65-brightgreen?style=for-the-badge
[tck-url]: https://github.com/sovra-dataspace/dataspace-core/blob/main/docs/tck.es.md
[dcp-tck-shield]: https://img.shields.io/badge/DCP_TCK-117%2F117-brightgreen?style=for-the-badge
[dcp-tck-url]: https://github.com/sovra-dataspace/dataspace-core/blob/main/docs/dcp.es.md#conformidad-el-tck-oficial-de-dcp
[license-shield]: https://img.shields.io/badge/licencia-Apache--2.0-blue?style=for-the-badge
[license-url]: https://github.com/sovra-dataspace/dataspace-core/blob/main/LICENSE
