# Memora (Re-Moment)

Choisir la langue:
[English](./README.md) | [한국어](./README_KO.md) | [日本語](./README_JA.md) | [简体中文](./README_ZH.md) | [Español](./README_ES.md) | [Français](./README_FR.md) | [Português](./README_PT.md) | [हिन्दी](./README_HI.md) | [বাংলা](./README_BN.md) | [العربية](./README_AR.md)

---

[![Platform: iOS 18+](https://img.shields.io/badge/Platform-iOS%2018%2B-blue.svg?style=flat-square&logo=apple)](https://developer.apple.com/ios/)
[![Platform: iPadOS 18+](https://img.shields.io/badge/Platform-iPadOS%2018%2B-blue.svg?style=flat-square&logo=apple)](https://developer.apple.com/ipados/)
[![Framework: Swift 6](https://img.shields.io/badge/Framework-Swift%206-orange.svg?style=flat-square&logo=swift)](https://developer.apple.com/swift/)
[![License: Proprietary](https://img.shields.io/badge/License-Proprietary-red.svg?style=flat-square)](./LICENSE.md)

Memora, nom de code interne **Re-Moment**, est une app iPhone et iPad local-first qui analyse la phototheque de l'utilisateur et transforme des moments lies en courtes videos de souvenirs. L'app met l'accent sur l'indexation privee des photos, les recommandations revisables, les brouillons d'histoires modifiables et le rendu sur l'appareil. Pro Vision AI est une option payante facultative pour des legendes de meilleure qualite et une indexation assistee a distance.

---

## Fonctionnalites principales

### Recommandations intelligentes d'histoires
* **Indexation de la phototheque:** Memora lit les photos autorisees avec PhotoKit et extrait des signaux de date, lieu, favori, type de media, qualite, nombre de visages, scene et legende.
* **Cartes de recommandation:** L'app cree des histoires candidates comme memes personnes, arrieres-plans similaires, repas, souvenirs saisonniers, ville/voyage, instantanes temporels, moments significatifs et temps forts video.
* **Recherche et maintenance:** Les photos indexees peuvent etre recherchees localement. L'app inclut aussi des actions de completement de traduction, reparation de coherence, reinitialisation des retours de recommandation et reprise de l'indexation.

### Histoires de souvenirs revisables
* **Revue d'histoire:** Avant le rendu, l'utilisateur peut inspecter une histoire suggeree, remplacer ou retirer des photos, ajouter des candidates, reordonner les elements et enregistrer des personnes representatives depuis des photos avec visages nets.
* **Controles de retour:** L'utilisateur peut archiver des histoires generees, masquer une recommandation specifique, masquer des types similaires et annuler un retour recent.
* **Support des personnes:** Les profils de personnes enregistres peuvent servir a creer des histoires centrees sur une personne et ameliorer les futures recommandations.

### Vision et stockage local-first
* **Par defaut sur l'appareil:** L'indexation standard et les legendes de secours utilisent PhotoKit, Vision et l'analyse de metadonnees locales. Les photos ne sont pas envoyees au serveur sauf si l'utilisateur active et utilise Pro Vision AI.
* **Base locale:** Memora stocke index, histoires, travaux de rendu, preferences, points de controle et profils de personnes dans le sandbox de l'app avec SwiftData. Si disponible, l'utilisateur peut choisir un stockage de base via iCloud Drive.
* **Diagnostics:** MetricKit sert a investiguer les crashs, blocages, lancements, CPU et problemes d'ecriture disque. Ces diagnostics n'incluent pas les fichiers photo originaux.

### Pro Vision AI
* **Fonction payante facultative:** Pro Vision AI utilise un proxy cote serveur pour des legendes VLM ameliorees et l'application de quotas d'indexation distante. Si le quota est indisponible ou le serveur inaccessible, l'app reste utilisable avec Vision AI locale standard.
* **Controle serveur:** Le backend verifie l'etat d'autorisation StoreKit, emet des jetons courts, applique les quotas, protege les cles API fournisseur, gere l'idempotence et suit les signaux anti-abus.
* **Traitement des images:** Les donnees d'image sont transmises uniquement pour l'operation de legende demandee. Le service est concu pour ne pas stocker les octets d'image originaux pour l'utilisation produit ou l'entrainement IA. Des enregistrements operationnels comme metadonnees de requete assainies, texte de reponse fournisseur, etat de requete, compteurs de quota, hachages d'appareil et erreurs peuvent etre conserves pour autorisation, quota, debogage, securite et prevention des abus.

### Rendu et sauvegarde video
* **Moteur de rendu natif:** Les histoires sont rendues avec AVFoundation a partir de photos mises en cache, avec une cible par defaut de 30fps et des effets comme dissolve, slide, wipe et zoom.
* **Export vers Photos:** Avant le rendu, Memora prepare des copies locales des elements iCloud-only si necessaire. Les videos rendues sont sauvegardees dans Photos avec l'autorisation add-only et un fallback MOV compatible Photos.
* **Progression et annulation:** L'app affiche les etats de telechargement, rendu, sauvegarde, echec, annulation et recuperation.

---

## Notes importantes

* Memora a besoin de l'acces en lecture a Photos pour indexer et recommander des histoires. L'acces limite est pris en charge, mais l'acces complet donne l'experience prevue.
* Sauvegarder des videos rendues necessite l'autorisation d'ajout a Photos.
* Pro Vision AI envoie les images selectionnees au backend et au fournisseur VLM configure. Utilisez-le uniquement pour des photos que vous acceptez de traiter a distance.
* Les legendes et recommandations generees par IA peuvent etre inexactes. Verifiez le contenu avant rendu ou partage.
* Le stockage via iCloud Drive depend de la configuration Apple iCloud et de la disponibilite de l'appareil.
* Noms de produit, quotas, prix et plateformes prises en charge peuvent changer avant ou apres la sortie App Store.

---

## Stack technique

### Client
* Swift 6, SwiftUI, SwiftData
* PhotoKit, Vision, AVFoundation, MetricKit
* Paquets lies a MLX Swift LM / MLX VLM, Swift HuggingFace, Swift Transformers

### Serveur
* FastAPI, Uvicorn, Starlette
* PostgreSQL, SQLAlchemy, Alembic, Psycopg 3
* Pydantic, Pydantic Settings, HTTPX
* PyJWT et cryptography pour les chemins de verification StoreKit et jetons

---

## Politiques et licences

* [Privacy Policy](./PRIVACY_POLICY.md)
* [Terms of Service](./TERMS_OF_SERVICE.md)
* [Legal Notice](./LEGAL_NOTICE.md)
* [Open Source Licenses](./OPEN_SOURCE_LICENSES.md)
* [Proprietary License](./LICENSE.md)

---

## Licence

Copyright (c) 2026 MFLab-AI. All rights reserved.

Le code source, les actifs, la marque, la documentation et les materiaux associes de Memora sont proprietaires sauf licence ecrite separee. Les composants open-source tiers restent soumis a leurs propres licences.
