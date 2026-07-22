# Awesome Pentest par IA [![Awesome](https://awesome.re/badge.svg)](https://awesome.re)

🌍 [English](README.md) · **Français** · [Español](README.es.md)

> Une liste curée d'outils de test d'intrusion propulsés par l'IA et les LLM : plateformes autonomes, assistants interactifs, benchmarks, et la recherche qui les sous-tend.

Le domaine est passé de vide à saturé en deux ans. Cette liste essaie d'en dresser une carte honnête : ce que chaque projet fait réellement, s'il est open source, et jusqu'où il va (web seulement, ou aussi Active Directory, Kubernetes et cloud). Pas de classement, pas de « celui-ci gagne ». Clonez les deux ou trois qui correspondent à vos contraintes et testez-les contre un lab que vous contrôlez.

Maintenue par l'équipe derrière [Darkmoon](https://github.com/ASCIT31/Dark-Moon) (listé plus bas, et signalé comme le nôtre). Les contributions d'outils qu'on aurait manqués, y compris des concurrents directs, sont les bienvenues. Voir [Contribuer](#contribuer).

## Sommaire

- [Comparatif](#comparatif)
- [Comment choisir](#comment-choisir)
- [Plateformes autonomes](#plateformes-autonomes)
- [Assistés par LLM (humain dans la boucle)](#assistés-par-llm-humain-dans-la-boucle)
- [Commercial](#commercial)
- [Benchmarks et évaluation](#benchmarks-et-évaluation)
- [Recherche et lectures](#recherche-et-lectures)
- [Contribuer](#contribuer)

## Comparatif

Les axes qui décident réellement d'un choix, pour les outils open source dont les capacités sont vérifiables depuis leur propre dépôt. Les outils commerciaux sont omis ici car leurs internes ne sont pas vérifiables depuis une source publique ; ils sont décrits [plus bas](#commercial). Corrections par PR bienvenues, et encouragées si vous maintenez l'un de ces outils.

Légende : ✅ oui · ➖ partiel ou indirect · ❌ pas une fonction annoncée

| Outil | Licence | Mode | Web/API | Active Directory | Kubernetes | Cloud | Preuve d'exploitation | Modèle local | Le modèle ne voit jamais les vraies données |
|------|---------|------|:-------:|:----------------:|:----------:|:-----:|:---------------------:|:-----------:|:--------------------------:|
| [Darkmoon](https://github.com/ASCIT31/Dark-Moon) † | GPL-3.0 | Autonome | ✅ | ✅ | ✅ | ➖ | ✅ | ✅ | ✅ |
| [Strix](https://github.com/usestrix/strix) | Apache-2.0 | Autonome | ✅ | ❌ | ❌ | ➖ | ✅ | ✅ | ❌ |
| [PentAGI](https://github.com/vxcontrol/pentagi) | MIT | Autonome | ✅ | ❌ | ❌ | ❌ | ➖ | ✅ | ➖ (air-gap) |
| [HexStrike AI](https://github.com/0x4m4/hexstrike-ai) | MIT | Autonome | ✅ | ✅ | ✅ | ✅ | ➖ | ❌ | ❌ |
| [CAI](https://github.com/aliasrobotics/cai) | MIT | Framework | ➖ | ➖ | ➖ | ➖ | ➖ | ✅ | ❌ |
| [PentestGPT](https://github.com/GreyDGL/PentestGPT) | MIT | Assisté | ✅ | ❌ | ❌ | ❌ | ➖ (humain) | ✅ | ❌ |
| [hackingBuddyGPT](https://github.com/ipa-lab/hackingBuddyGPT) | MIT | Assisté | ➖ | ➖ (escalade) | ❌ | ❌ | ➖ | ✅ | ❌ |

† Maintenu par nous. C'est nous qui avons construit ce tableau, donc lisez notre ligne avec la méfiance qui s'impose et vérifiez par vous-même. Quelques notes honnêtes pour que ce ne soit pas un score truqué : **HexStrike AI** a la couverture d'outils brute la plus large ici et nous égale ou nous dépasse sur l'étendue du périmètre. **Strix** est autonome avec de vraies PoC et plus abouti sur le test web pur. Plusieurs outils tournent sur modèle local comme nous. La seule colonne où le champ est réellement vide, c'est la dernière : garder un modèle frontier dans la boucle pendant que le modèle ne voit jamais une vraie IP, un nom d'hôte ou un identifiant. C'est le problème qu'on a voulu résoudre, et si quelqu'un le résout aussi, on cochera sa case avec plaisir.

## Comment choisir

- **Web uniquement, agent autonome solide :** Strix ou PentAGI.
- **Couverture d'outils la plus large d'emblée :** HexStrike AI.
- **Apprentissage, ou travail type CTF avec un humain aux commandes :** PentestGPT ou hackingBuddyGPT.
- **Construire ses propres agents :** CAI.
- **Active Directory et Kubernetes plus confidentialité stricte des données :** Darkmoon.
- **Vous pouvez accepter un fournisseur SaaS et un budget :** les plateformes commerciales ci-dessous.

Tous les outils open source sont libres à cloner, donc la recommandation honnête est de tester les deux ou trois qui correspondent à vos contraintes contre un lab que vous possédez, plutôt que de faire confiance à un tableau, celui-ci compris.

## Plateformes autonomes

Des outils qui prennent une cible, raisonnent dessus avec un modèle, et lancent réellement l'outillage offensif au lieu de seulement suggérer des commandes.

- [Darkmoon](https://github.com/ASCIT31/Dark-Moon) - Plateforme GPL-3.0 et hôte MCP avec des sous-agents par technologie. Couvre web, API, Active Directory et Kubernetes ; chaque découverte porte la commande exécutée et sa sortie ; une passerelle de confidentialité tient les vraies IP, hôtes et identifiants à l'écart du modèle. *(Divulgation complète : maintenu par nous.)*
- [Strix](https://github.com/usestrix/strix) - Agents autonomes Apache-2.0 centrés sur le test d'applications web.
- [PentAGI](https://github.com/vxcontrol/pentagi) - Framework entièrement autonome avec orchestrateur et graphe de mémoire, basé conteneur.
- [CAI](https://github.com/aliasrobotics/cai) - Framework pour construire des agents autonomes de test de sécurité, avec son propre travail de benchmark.
- [HexStrike AI](https://github.com/0x4m4/hexstrike-ai) - Agent autonome reliant un LLM à une large boîte à outils offensive.

## Assistés par LLM (humain dans la boucle)

Assistants interactifs qui guident un humain ; vous restez aux commandes et lancez les outils.

- [PentestGPT](https://github.com/GreyDGL/PentestGPT) - Le projet qui a lancé la vague. Assistant interactif qui vous guide dans un pentest. Excellent pour l'apprentissage et le travail type CTF.
- [hackingBuddyGPT](https://github.com/ipa-lab/hackingBuddyGPT) - Académique, ciblé et honnête. Bon pour étudier jusqu'où un petit modèle va sur l'escalade de privilèges, avec des chiffres publiés.
- [HackerAI](https://hackerai.co/) - Assistant de test d'intrusion propulsé par l'IA.

## Commercial

Sources fermées, listés par souci d'exhaustivité parce que les gens s'y comparent.

- [XBOW](https://xbow.com/) - Plateforme de sécurité offensive autonome ; a notamment dominé un classement HackerOne.
- [NodeZero](https://www.horizon3.ai/) - Plateforme de pentest et validation autonome de Horizon3.ai.
- [Pentera](https://pentera.io/) - Plateforme de validation de sécurité automatisée.

## Benchmarks et évaluation

- [AutoPenBench](https://github.com/lucagioacchini/auto-pen-bench) - Benchmark pour agents génératifs en test d'intrusion automatisé.
- [CVE-Bench](https://github.com/uiuc-kang-lab/cve-bench) - Benchmark de la capacité des agents IA à exploiter de vraies vulnérabilités web.
- [PACEbench](https://arxiv.org/abs/2510.11688) - Cadre d'évaluation de l'exploitation cyber par IA en pratique.

## Recherche et lectures

- [A Survey of LLM-Driven Penetration Testing](https://arxiv.org/abs/2607.02605) - Taxonomie, co-évolution et défis ouverts. Une bonne première lecture pour tout le domaine.
- [Comment mener un pentest IA sans envoyer vos données au LLM](https://dark-moon.org/blog/ai-pentest-without-sending-data-to-the-llm/) - Article de conception sur le problème d'exposition des données (par l'équipe Darkmoon).

## Contribuer

Les pull requests sont bienvenues. Une entrée par outil, l'ordre alphabétique dans une section n'est pas requis mais gardez des descriptions factuelles sur une ligne. Les concurrents et les outils commerciaux sont explicitement dans le périmètre ; cette liste est d'autant plus utile qu'elle est complète et neutre. Si vous maintenez un outil listé ici et souhaitez modifier la description, ouvrez une PR.

## Licence

[![CC0](https://licensebuttons.net/p/zero/1.0/88x31.png)](https://creativecommons.org/publicdomain/zero/1.0/)

Dans la mesure permise par la loi, les contributeurs ont renoncé à tous droits d'auteur et droits voisins sur ce travail.
