# Awesome Pentest con IA [![Awesome](https://awesome.re/badge.svg)](https://awesome.re)

🌍 [English](README.md) · [Français](README.fr.md) · **Español** · [Português](README.pt.md) · [Deutsch](README.de.md)

> Una lista curada de herramientas de pentesting impulsadas por IA y LLM: plataformas autónomas, asistentes interactivos, benchmarks y la investigación que las respalda.

El campo pasó de vacío a saturado en unos dos años. Esta lista intenta ser un mapa honesto: qué hace realmente cada proyecto, si es open source, y hasta dónde llega (solo web, o también Active Directory, Kubernetes y cloud). Sin rankings, sin «este gana». Clona los dos o tres que encajen con tus restricciones y pruébalos contra un laboratorio que controles.

Mantenida por el equipo detrás de [Darkmoon](https://github.com/ASCIT31/Dark-Moon) (listado abajo, y señalado como nuestro). Las contribuciones de herramientas que hayamos omitido, incluidos competidores directos, son muy bienvenidas. Ver [Contribuir](#contribuir).

## Contenido

- [Comparativa](#comparativa)
- [Cómo elegir](#cómo-elegir)
- [Plataformas autónomas](#plataformas-autónomas)
- [Asistidas por LLM (humano en el bucle)](#asistidas-por-llm-humano-en-el-bucle)
- [Comercial](#comercial)
- [Benchmarks y evaluación](#benchmarks-y-evaluación)
- [Investigación y lecturas](#investigación-y-lecturas)
- [Contribuir](#contribuir)

## Comparativa

Los ejes que realmente deciden una elección, para las herramientas open source cuyas capacidades pueden verificarse desde su propio repositorio. Las herramientas comerciales se omiten aquí porque sus internos no se pueden verificar de forma independiente desde fuente pública; se describen [más abajo](#comercial). Correcciones vía PR bienvenidas, y alentadas si mantienes una de estas.

Leyenda: ✅ sí · ➖ parcial o indirecto · ❌ no es una función declarada

| Herramienta | Licencia | Modo | Web/API | Active Directory | Kubernetes | Cloud | Prueba de explotación | Modelo local | El modelo nunca ve datos reales |
|------|---------|------|:-------:|:----------------:|:----------:|:-----:|:---------------------:|:-----------:|:--------------------------:|
| [Darkmoon](https://github.com/ASCIT31/Dark-Moon) † | GPL-3.0 | Autónomo | ✅ | ✅ | ✅ | ➖ | ✅ | ✅ | ✅ |
| [Strix](https://github.com/usestrix/strix) | Apache-2.0 | Autónomo | ✅ | ❌ | ❌ | ➖ | ✅ | ✅ | ❌ |
| [PentAGI](https://github.com/vxcontrol/pentagi) | MIT | Autónomo | ✅ | ❌ | ❌ | ❌ | ➖ | ✅ | ➖ (air-gap) |
| [HexStrike AI](https://github.com/0x4m4/hexstrike-ai) | MIT | Autónomo | ✅ | ✅ | ✅ | ✅ | ➖ | ❌ | ❌ |
| [CAI](https://github.com/aliasrobotics/cai) | MIT | Framework | ➖ | ➖ | ➖ | ➖ | ➖ | ✅ | ❌ |
| [PentestGPT](https://github.com/GreyDGL/PentestGPT) | MIT | Asistido | ✅ | ❌ | ❌ | ❌ | ➖ (humano) | ✅ | ❌ |
| [hackingBuddyGPT](https://github.com/ipa-lab/hackingBuddyGPT) | MIT | Asistido | ➖ | ➖ (escalada) | ❌ | ❌ | ➖ | ✅ | ❌ |

† Mantenido por nosotros. Construimos la matriz, así que lee nuestra fila con la desconfianza apropiada y verifícala tú mismo. Algunas notas honestas para que no sea un marcador amañado: **HexStrike AI** tiene la cobertura de herramientas más amplia aquí y nos iguala o supera en amplitud de alcance. **Strix** es autónomo con PoCs reales y más pulido en pruebas web puras. Varias herramientas ejecutan modelos locales igual que nosotros. La única columna donde el campo está realmente vacío es la última: mantener un modelo frontier en el bucle mientras el modelo nunca ve una IP, un nombre de host o una credencial real. Ese es el problema que nos propusimos resolver, y si alguien más lo resuelve, marcaremos su casilla con gusto.

## Cómo elegir

- **Solo web, quieres un agente autónomo potente:** Strix o PentAGI.
- **Mayor cobertura de herramientas de fábrica:** HexStrike AI.
- **Aprendizaje, o trabajo tipo CTF con un humano al mando:** PentestGPT o hackingBuddyGPT.
- **Construir tus propios agentes:** CAI.
- **Active Directory y Kubernetes más privacidad estricta de datos:** Darkmoon.
- **Puedes aceptar un proveedor SaaS y un presupuesto:** las plataformas comerciales de abajo.

Todas las open source son libres de clonar, así que la recomendación honesta es probar las dos o tres que encajen con tus restricciones contra un laboratorio que poseas, en lugar de fiarte de una tabla, incluida esta.

## Plataformas autónomas

Herramientas que toman un objetivo, razonan sobre él con un modelo y ejecutan realmente utillaje ofensivo en vez de solo sugerir comandos.

- [Darkmoon](https://github.com/ASCIT31/Dark-Moon) - Plataforma GPL-3.0 y host MCP con subagentes por tecnología. Cubre web, API, Active Directory y Kubernetes; cada hallazgo lleva el comando ejecutado y su salida; una pasarela de privacidad mantiene las IP, hosts y credenciales reales fuera del alcance del modelo. *(Divulgación completa: mantenido por nosotros.)*
- [Strix](https://github.com/usestrix/strix) - Agentes autónomos Apache-2.0 centrados en pruebas de aplicaciones web.
- [PentAGI](https://github.com/vxcontrol/pentagi) - Framework totalmente autónomo con orquestador y grafo de memoria, basado en contenedores.
- [CAI](https://github.com/aliasrobotics/cai) - Framework para construir agentes autónomos de pruebas de seguridad, con su propio trabajo de benchmark.
- [HexStrike AI](https://github.com/0x4m4/hexstrike-ai) - Agente autónomo que conecta un LLM a una amplia caja de herramientas ofensivas.

## Asistidas por LLM (humano en el bucle)

Asistentes interactivos que guían a un humano; te quedas al mando y ejecutas las herramientas.

- [PentestGPT](https://github.com/GreyDGL/PentestGPT) - El proyecto que inició la ola. Asistente interactivo que te guía en un pentest. Excelente para aprender y para trabajo tipo CTF.
- [hackingBuddyGPT](https://github.com/ipa-lab/hackingBuddyGPT) - Académico, enfocado y honesto. Bueno para estudiar hasta dónde llega un modelo pequeño en escalada de privilegios, con números publicados.
- [HackerAI](https://hackerai.co/) - Asistente de pentesting impulsado por IA.

## Comercial

Código cerrado, listados por exhaustividad porque la gente se compara con ellos.

- [XBOW](https://xbow.com/) - Plataforma autónoma de seguridad ofensiva; encabezó un ranking de HackerOne.
- [NodeZero](https://www.horizon3.ai/) - Plataforma de pentest y validación autónoma de Horizon3.ai.
- [Pentera](https://pentera.io/) - Plataforma de validación de seguridad automatizada.

## Benchmarks y evaluación

- [AutoPenBench](https://github.com/lucagioacchini/auto-pen-bench) - Benchmark para agentes generativos en pentesting automatizado.
- [CVE-Bench](https://github.com/uiuc-kang-lab/cve-bench) - Benchmark de la capacidad de agentes IA para explotar vulnerabilidades web reales.
- [PACEbench](https://arxiv.org/abs/2510.11688) - Marco para evaluar la explotación cibernética por IA en la práctica.

## Investigación y lecturas

- [A Survey of LLM-Driven Penetration Testing](https://arxiv.org/abs/2607.02605) - Taxonomía, coevolución y desafíos abiertos. Una buena primera lectura para todo el campo.
- [Cómo hacer un pentest con IA sin enviar tus datos al LLM](https://dark-moon.org/blog/ai-pentest-without-sending-data-to-the-llm/) - Artículo de diseño sobre el problema de exposición de datos (por el equipo de Darkmoon).

## Contribuir

Las pull requests son bienvenidas. Una entrada por herramienta, el orden alfabético dentro de una sección no es obligatorio pero mantén las descripciones factuales y en una línea. Los competidores y las herramientas comerciales están explícitamente dentro del alcance; esta lista es más útil cuanto más completa y neutral sea. Si mantienes una herramienta listada aquí y quieres cambiar la descripción, abre una PR.

## Licencia

[![CC0](https://licensebuttons.net/p/zero/1.0/88x31.png)](https://creativecommons.org/publicdomain/zero/1.0/)

En la medida de lo posible bajo la ley, los contribuyentes han renunciado a todos los derechos de autor y derechos conexos sobre este trabajo.
