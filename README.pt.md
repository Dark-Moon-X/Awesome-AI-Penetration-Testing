# Awesome Pentest com IA [![Awesome](https://awesome.re/badge.svg)](https://awesome.re)

🌍 [English](README.md) · [Français](README.fr.md) · [Español](README.es.md) · **Português**

> Uma lista curada de ferramentas de pentest com IA e LLM: plataformas autónomas, assistentes interativos, benchmarks e a investigação por trás delas.

O campo passou de vazio a saturado em cerca de dois anos. Esta lista tenta ser um mapa honesto: o que cada projeto faz de facto, se é open source, e até onde vai (só web, ou também Active Directory, Kubernetes e cloud). Sem rankings, sem «este ganha». Clona os dois ou três que se ajustam às tuas restrições e testa-os contra um laboratório que controles.

Mantida pela equipa por trás do [Darkmoon](https://github.com/ASCIT31/Dark-Moon) (listado abaixo, e assinalado como nosso). Contribuições de ferramentas que tenhamos omitido, incluindo concorrentes diretos, são muito bem-vindas. Ver [Contribuir](#contribuir).

## Conteúdo

- [Comparação](#comparação)
- [Como escolher](#como-escolher)
- [Plataformas autónomas](#plataformas-autónomas)
- [Assistidas por LLM (humano no ciclo)](#assistidas-por-llm-humano-no-ciclo)
- [Comercial](#comercial)
- [Benchmarks e avaliação](#benchmarks-e-avaliação)
- [Investigação e leituras](#investigação-e-leituras)
- [Contribuir](#contribuir)

## Comparação

Os eixos que realmente decidem uma escolha, para as ferramentas open source cujas capacidades podem ser verificadas a partir do próprio repositório. As ferramentas comerciais são omitidas aqui porque os seus internos não podem ser verificados de forma independente a partir de fonte pública; são descritas [mais abaixo](#comercial). Correções via PR são bem-vindas, e encorajadas se manténs uma destas.

Legenda: ✅ sim · ➖ parcial ou indireto · ❌ não é uma funcionalidade declarada

| Ferramenta | Licença | Modo | Web/API | Active Directory | Kubernetes | Cloud | Prova de exploração | Modelo local | O modelo nunca vê dados reais |
|------|---------|------|:-------:|:----------------:|:----------:|:-----:|:---------------------:|:-----------:|:--------------------------:|
| [Darkmoon](https://github.com/ASCIT31/Dark-Moon) † | GPL-3.0 | Autónomo | ✅ | ✅ | ✅ | ➖ | ✅ | ✅ | ✅ |
| [Strix](https://github.com/usestrix/strix) | Apache-2.0 | Autónomo | ✅ | ❌ | ❌ | ➖ | ✅ | ✅ | ❌ |
| [PentAGI](https://github.com/vxcontrol/pentagi) | MIT | Autónomo | ✅ | ❌ | ❌ | ❌ | ➖ | ✅ | ➖ (air-gap) |
| [HexStrike AI](https://github.com/0x4m4/hexstrike-ai) | MIT | Autónomo | ✅ | ✅ | ✅ | ✅ | ➖ | ❌ | ❌ |
| [CAI](https://github.com/aliasrobotics/cai) | MIT | Framework | ➖ | ➖ | ➖ | ➖ | ➖ | ✅ | ❌ |
| [PentestGPT](https://github.com/GreyDGL/PentestGPT) | MIT | Assistido | ✅ | ❌ | ❌ | ❌ | ➖ (humano) | ✅ | ❌ |
| [hackingBuddyGPT](https://github.com/ipa-lab/hackingBuddyGPT) | MIT | Assistido | ➖ | ➖ (escalada) | ❌ | ❌ | ➖ | ✅ | ❌ |

† Mantido por nós. Construímos a matriz, por isso lê a nossa linha com a desconfiança apropriada e verifica-a tu mesmo. Algumas notas honestas para que não seja um placar viciado: **HexStrike AI** tem a cobertura de ferramentas mais ampla aqui e iguala-nos ou supera-nos na amplitude de alcance. **Strix** é autónomo com PoCs reais e mais polido em testes web puros. Várias ferramentas correm modelos locais tal como nós. A única coluna onde o campo está realmente vazio é a última: manter um modelo frontier no ciclo enquanto o modelo nunca vê um IP, um nome de host ou uma credencial real. Esse é o problema que nos propusemos resolver, e se alguém o resolver também, marcaremos a sua casa com prazer.

## Como escolher

- **Só web, queres um agente autónomo forte:** Strix ou PentAGI.
- **Maior cobertura de ferramentas de origem:** HexStrike AI.
- **Aprendizagem, ou trabalho tipo CTF com um humano ao comando:** PentestGPT ou hackingBuddyGPT.
- **Construir os teus próprios agentes:** CAI.
- **Active Directory e Kubernetes mais privacidade estrita de dados:** Darkmoon.
- **Podes aceitar um fornecedor SaaS e um orçamento:** as plataformas comerciais abaixo.

Todas as open source são livres de clonar, por isso a recomendação honesta é testar as duas ou três que se ajustam às tuas restrições contra um laboratório que possuas, em vez de confiar numa tabela, incluindo esta.

## Plataformas autónomas

Ferramentas que pegam num alvo, raciocinam sobre ele com um modelo, e executam de facto ferramentas ofensivas em vez de apenas sugerir comandos.

- [Darkmoon](https://github.com/ASCIT31/Dark-Moon) - Plataforma GPL-3.0 e host MCP com subagentes por tecnologia. Cobre web, API, Active Directory e Kubernetes; cada achado traz o comando executado e a sua saída; uma gateway de privacidade mantém os IPs, hosts e credenciais reais fora do alcance do modelo. *(Divulgação total: mantido por nós.)*
- [Strix](https://github.com/usestrix/strix) - Agentes autónomos Apache-2.0 focados em testes de aplicações web.
- [PentAGI](https://github.com/vxcontrol/pentagi) - Framework totalmente autónomo com orquestrador e grafo de memória, baseado em contentores.
- [CAI](https://github.com/aliasrobotics/cai) - Framework para construir agentes autónomos de testes de segurança, com o seu próprio trabalho de benchmark.
- [HexStrike AI](https://github.com/0x4m4/hexstrike-ai) - Agente autónomo que liga um LLM a uma ampla caixa de ferramentas ofensivas.

## Assistidas por LLM (humano no ciclo)

Assistentes interativos que guiam um humano; ficas ao comando e executas as ferramentas.

- [PentestGPT](https://github.com/GreyDGL/PentestGPT) - O projeto que iniciou a onda. Assistente interativo que te guia num pentest. Excelente para aprender e para trabalho tipo CTF.
- [hackingBuddyGPT](https://github.com/ipa-lab/hackingBuddyGPT) - Académico, focado e honesto. Bom para estudar até onde um modelo pequeno chega em escalada de privilégios, com números publicados.
- [HackerAI](https://hackerai.co/) - Assistente de pentest com IA.

## Comercial

Código fechado, listados por exaustividade porque as pessoas comparam-se com eles.

- [XBOW](https://xbow.com/) - Plataforma autónoma de segurança ofensiva; liderou um ranking da HackerOne.
- [NodeZero](https://www.horizon3.ai/) - Plataforma de pentest e validação autónoma da Horizon3.ai.
- [Pentera](https://pentera.io/) - Plataforma de validação de segurança automatizada.

## Benchmarks e avaliação

- [AutoPenBench](https://github.com/lucagioacchini/auto-pen-bench) - Benchmark para agentes generativos em pentest automatizado.
- [CVE-Bench](https://github.com/uiuc-kang-lab/cve-bench) - Benchmark da capacidade de agentes IA para explorar vulnerabilidades web reais.
- [PACEbench](https://arxiv.org/abs/2510.11688) - Framework para avaliar a exploração cibernética por IA na prática.

## Investigação e leituras

- [A Survey of LLM-Driven Penetration Testing](https://arxiv.org/abs/2607.02605) - Taxonomia, coevolução e desafios abertos. Uma boa primeira leitura para todo o campo.
- [Como fazer um pentest com IA sem enviar os teus dados ao LLM](https://dark-moon.org/blog/ai-pentest-without-sending-data-to-the-llm/) - Artigo de design sobre o problema de exposição de dados (pela equipa Darkmoon).

## Contribuir

Pull requests são bem-vindas. Uma entrada por ferramenta, a ordem alfabética dentro de uma secção não é obrigatória mas mantém as descrições factuais e numa linha. Concorrentes e ferramentas comerciais estão explicitamente no âmbito; esta lista é mais útil quanto mais completa e neutra for. Se manténs uma ferramenta listada aqui e queres mudar a descrição, abre uma PR.

## Licença

[![CC0](https://licensebuttons.net/p/zero/1.0/88x31.png)](https://creativecommons.org/publicdomain/zero/1.0/)

Na medida do permitido por lei, os contribuidores renunciaram a todos os direitos de autor e direitos conexos sobre este trabalho.
