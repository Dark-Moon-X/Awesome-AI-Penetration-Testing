# Awesome KI-Pentesting [![Awesome](https://awesome.re/badge.svg)](https://awesome.re)

🌍 [English](README.md) · [Français](README.fr.md) · [Español](README.es.md) · [Português](README.pt.md) · **Deutsch**

> Eine kuratierte Liste von KI- und LLM-gestützten Pentesting-Werkzeugen: autonome Plattformen, interaktive Assistenten, Benchmarks und die Forschung dahinter.

Das Feld ging in etwa zwei Jahren von leer zu überfüllt. Diese Liste versucht, eine ehrliche Karte zu sein: was jedes Projekt tatsächlich tut, ob es Open Source ist und wie weit es reicht (nur Web, oder auch Active Directory, Kubernetes und Cloud). Keine Ranglisten, kein «dieses gewinnt». Klone die zwei oder drei, die zu deinen Rahmenbedingungen passen, und teste sie gegen ein Labor, das du kontrollierst.

Gepflegt vom Team hinter [Darkmoon](https://github.com/ASCIT31/Dark-Moon) (unten gelistet und als unseres gekennzeichnet). Beiträge zu Werkzeugen, die wir übersehen haben, einschließlich direkter Konkurrenten, sind sehr willkommen. Siehe [Mitwirken](#mitwirken).

## Inhalt

- [Vergleich](#vergleich)
- [Wie wählen](#wie-wählen)
- [Autonome Plattformen](#autonome-plattformen)
- [LLM-unterstützt (Mensch im Loop)](#llm-unterstützt-mensch-im-loop)
- [Kommerziell](#kommerziell)
- [Benchmarks und Evaluierung](#benchmarks-und-evaluierung)
- [Forschung und Lektüre](#forschung-und-lektüre)
- [Mitwirken](#mitwirken)

## Vergleich

Die Achsen, die eine Wahl wirklich entscheiden, für die Open-Source-Werkzeuge, deren Fähigkeiten aus ihrem eigenen Repository überprüfbar sind. Kommerzielle Werkzeuge werden hier ausgelassen, da ihre Interna nicht unabhängig aus öffentlicher Quelle überprüfbar sind; sie werden [unten](#kommerziell) beschrieben. Korrekturen per PR sind willkommen und erwünscht, wenn du eines davon pflegst.

Legende: ✅ ja · ➖ teilweise oder indirekt · ❌ keine angegebene Funktion

| Werkzeug | Lizenz | Modus | Web/API | Active Directory | Kubernetes | Cloud | Exploit-Nachweis | Lokales Modell | Modell sieht nie echte Daten |
|------|---------|------|:-------:|:----------------:|:----------:|:-----:|:---------------------:|:-----------:|:--------------------------:|
| [Darkmoon](https://github.com/ASCIT31/Dark-Moon) † | GPL-3.0 | Autonom | ✅ | ✅ | ✅ | ➖ | ✅ | ✅ | ✅ |
| [Strix](https://github.com/usestrix/strix) | Apache-2.0 | Autonom | ✅ | ❌ | ❌ | ➖ | ✅ | ✅ | ❌ |
| [PentAGI](https://github.com/vxcontrol/pentagi) | MIT | Autonom | ✅ | ❌ | ❌ | ❌ | ➖ | ✅ | ➖ (air-gap) |
| [HexStrike AI](https://github.com/0x4m4/hexstrike-ai) | MIT | Autonom | ✅ | ✅ | ✅ | ✅ | ➖ | ❌ | ❌ |
| [CAI](https://github.com/aliasrobotics/cai) | MIT | Framework | ➖ | ➖ | ➖ | ➖ | ➖ | ✅ | ❌ |
| [PentestGPT](https://github.com/GreyDGL/PentestGPT) | MIT | Assistiert | ✅ | ❌ | ❌ | ❌ | ➖ (Mensch) | ✅ | ❌ |
| [hackingBuddyGPT](https://github.com/ipa-lab/hackingBuddyGPT) | MIT | Assistiert | ➖ | ➖ (Priv-Esc) | ❌ | ❌ | ➖ | ✅ | ❌ |

† Von uns gepflegt. Wir haben die Matrix erstellt, also lies unsere Zeile mit angemessenem Misstrauen und prüfe sie selbst. Ein paar ehrliche Anmerkungen, damit es keine manipulierte Wertung ist: **HexStrike AI** hat hier die breiteste reine Werkzeugabdeckung und erreicht oder übertrifft uns bei der Reichweite. **Strix** ist autonom mit echten PoCs und ausgereifter bei reinen Web-Tests. Mehrere Werkzeuge laufen mit lokalen Modellen genau wie wir. Die einzige Spalte, in der das Feld wirklich leer ist, ist die letzte: ein Frontier-Modell im Loop zu halten, während das Modell nie eine echte IP, einen Hostnamen oder eine Anmeldeinformation sieht. Das ist das Problem, das wir lösen wollten, und wenn es jemand auch löst, setzen wir gern das Häkchen.

## Wie wählen

- **Nur Web, starker autonomer Agent gewünscht:** Strix oder PentAGI.
- **Breiteste Werkzeugabdeckung von Haus aus:** HexStrike AI.
- **Lernen oder CTF-artige Arbeit mit einem Menschen am Steuer:** PentestGPT oder hackingBuddyGPT.
- **Eigene Agenten bauen:** CAI.
- **Active Directory und Kubernetes plus strikter Datenschutz:** Darkmoon.
- **Ein SaaS-Anbieter und Budget sind akzeptabel:** die kommerziellen Plattformen unten.

Alle Open-Source-Werkzeuge sind frei klonbar, daher die ehrliche Empfehlung: teste die zwei oder drei, die zu deinen Rahmenbedingungen passen, gegen ein eigenes Labor, statt einer Tabelle zu vertrauen, auch dieser.

## Autonome Plattformen

Werkzeuge, die ein Ziel nehmen, mit einem Modell darüber nachdenken und tatsächlich offensive Werkzeuge ausführen, statt nur Befehle vorzuschlagen.

- [Darkmoon](https://github.com/ASCIT31/Dark-Moon) - GPL-3.0-Plattform und MCP-Host mit Subagenten pro Technologie. Deckt Web, API, Active Directory und Kubernetes ab; jeder Fund enthält den ausgeführten Befehl und dessen Ausgabe; ein Privacy-Gateway hält echte IPs, Hosts und Anmeldeinformationen vom Modell fern. *(Volle Offenlegung: von uns gepflegt.)*
- [Strix](https://github.com/usestrix/strix) - Autonome Apache-2.0-Agenten mit Fokus auf Web-Anwendungstests.
- [PentAGI](https://github.com/vxcontrol/pentagi) - Vollständig autonomes Framework mit Orchestrator und Speichergraph, containerbasiert.
- [CAI](https://github.com/aliasrobotics/cai) - Framework zum Bau autonomer Sicherheitstest-Agenten, mit eigener Benchmark-Arbeit.
- [HexStrike AI](https://github.com/0x4m4/hexstrike-ai) - Autonomer Agent, der ein LLM mit einem großen Werkzeugkasten offensiver Werkzeuge verbindet.

## LLM-unterstützt (Mensch im Loop)

Interaktive Assistenten, die einen Menschen anleiten; du bleibst am Steuer und führst die Werkzeuge aus.

- [PentestGPT](https://github.com/GreyDGL/PentestGPT) - Das Projekt, das die Welle auslöste. Interaktiver Assistent, der dich durch einen Pentest führt. Hervorragend zum Lernen und für CTF-artige Arbeit.
- [hackingBuddyGPT](https://github.com/ipa-lab/hackingBuddyGPT) - Akademisch, fokussiert und ehrlich. Gut, um zu untersuchen, wie weit ein kleines Modell bei Privilegieneskalation kommt, mit veröffentlichten Zahlen.
- [HackerAI](https://hackerai.co/) - KI-gestützter Pentest-Assistent.

## Kommerziell

Closed Source, der Vollständigkeit halber gelistet, weil man sich mit ihnen vergleicht.

- [XBOW](https://xbow.com/) - Autonome Offensive-Security-Plattform; führte eine HackerOne-Rangliste an.
- [NodeZero](https://www.horizon3.ai/) - Autonome Pentest- und Validierungsplattform von Horizon3.ai.
- [Pentera](https://pentera.io/) - Automatisierte Security-Validierungsplattform.

## Benchmarks und Evaluierung

- [AutoPenBench](https://github.com/lucagioacchini/auto-pen-bench) - Benchmark für generative Agenten im automatisierten Pentesting.
- [CVE-Bench](https://github.com/uiuc-kang-lab/cve-bench) - Benchmark für die Fähigkeit von KI-Agenten, echte Web-Schwachstellen auszunutzen.
- [PACEbench](https://arxiv.org/abs/2510.11688) - Framework zur Bewertung praktischer KI-Cyber-Exploitation.

## Forschung und Lektüre

- [A Survey of LLM-Driven Penetration Testing](https://arxiv.org/abs/2607.02605) - Taxonomie, Ko-Evolution und offene Herausforderungen. Ein guter erster Einstieg ins gesamte Feld.
- [Wie man einen KI-Pentest durchführt, ohne seine Daten an das LLM zu senden](https://dark-moon.org/blog/ai-pentest-without-sending-data-to-the-llm/) - Design-Artikel zum Datenexpositionsproblem (vom Darkmoon-Team).

## Mitwirken

Pull Requests sind willkommen. Ein Eintrag pro Werkzeug, alphabetische Reihenfolge innerhalb eines Abschnitts ist nicht erforderlich, aber halte die Beschreibungen sachlich und einzeilig. Konkurrenten und kommerzielle Werkzeuge sind ausdrücklich im Umfang; diese Liste ist umso nützlicher, je vollständiger und neutraler sie ist. Wenn du ein hier gelistetes Werkzeug pflegst und die Beschreibung ändern möchtest, öffne eine PR.

## Lizenz

[![CC0](https://licensebuttons.net/p/zero/1.0/88x31.png)](https://creativecommons.org/publicdomain/zero/1.0/)

Soweit gesetzlich möglich, haben die Mitwirkenden auf alle Urheber- und verwandten Rechte an diesem Werk verzichtet.
