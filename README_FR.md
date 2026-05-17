# Memora (Re-Moment)

🌐 **Select Language / 언어 선택:**
[English](./README.md) | [한국어](./README_KO.md) | [日本語](./README_JA.md) | [简体中文](./README_ZH.md) | [Español](./README_ES.md) | [Français](./README_FR.md) | [Português](./README_PT.md) | [हिन्दी](./README_HI.md) | [বাংলা](./README_BN.md) | [العربية](./README_AR.md)

---

[![Platform: iOS 18+](https://img.shields.io/badge/Platform-iOS%2018%2B-blue.svg?style=flat-square&logo=apple)](https://developer.apple.com/ios/)
[![Platform: macOS 15+](https://img.shields.io/badge/Platform-macOS%2015%2B-lightgrey.svg?style=flat-square&logo=apple)](https://developer.apple.com/macos/)
[![Framework: Swift 6](https://img.shields.io/badge/Framework-Swift%206-orange.svg?style=flat-square&logo=swift)](https://developer.apple.com/swift/)
[![License: Proprietary](https://img.shields.io/badge/License-Proprietary-red.svg?style=flat-square)](./LICENSE)

Memora (nom de code interne **Re-Moment**) est un compagnon de récits photo et de collections intelligentes respectueux de la vie privée, propulsé par une IA locale sur l'appareil. Il permet aux utilisateurs de regrouper automatiquement, de légender élégamment et de restituer de manière dynamique des diaporamas cinématographiques de leurs souvenirs personnels, tout en garantissant que leurs photos et métadonnées restent strictement sous leur propre contrôle exclusif.

---

## 📸 Fonctionnalités Clés (Core Features)

### 🧠 Collections Intelligentes Spatio-Temporelles
* **Moteur de Regroupement et de Recommandation :** Regroupe automatiquement les médias à l'aide d'algorithmes sophistiqués basés sur des seuils spatiaux (localisation géographique) et temporels (intervalles de temps) en événements cohérents et contextuels (ex. *"Week-end à Paris"*, *"Pique-nique d'été"*).
* **Diversification Thématique :** Combine les préférences de l'utilisateur, les métadonnées d'origine des photos et les caractéristiques visuelles pour générer des cartes résumé et des signaux de collection intelligents et structurés.

### 🛡️ IA de Vision Locale sur l'Appareil (On-Device Vision AI)
* **Indexation sans Connaissance (Zero-Knowledge Indexing) :** Réalise le regroupement facial principal, l'indexation des caractéristiques et la reconnaissance d'objets entièrement sur l'appareil en utilisant les frameworks d'apprentissage automatique locaux d'Apple (**CoreML**, **Vision** et les exécuteurs locaux **MLX Swift / MLX Swift LM / MLX VLM**). Aucune photo ne quitte l'appareil.
* **Stockage Local des Métadonnées Sécurisées :** Génère des descriptions, des légendes et des historiques qui sont stockés en toute sécurité dans l'espace isolé (sandbox) de l'appareil ou synchronisés via le compte personnel **Apple iCloud** de l'utilisateur si cette option est activée.

### ⚡ Pro Vision AI (VLM Assistée par le Cloud)
* **Légendes de Haute Fidélité :** Fonctionnalité premium optionnelle fournissant des légendes descriptives enrichies et des balises détaillées adaptées au contexte en utilisant des Modèles de Langage et de Vision (VLM) avancés.
* **Politique de Zéro Rétention en Mémoire (In-Memory Zero-Retention Policy) :** Les images transmises à nos serveurs sont traitées strictement dans la mémoire RAM temporaire et sont **supprimées à 100 % de manière permanente** immédiatement après le retour de la légende générée. Aucune photo n'est stockée, aucun journal n'est enregistré et elles ne sont jamais utilisées pour l'entraînement de l'IA.

### 🎬 Rendu de Diaporamas Cinématographiques
* **Moteur de Transitions Dynamiques :** Assemble automatiquement les photos d'une histoire en vidéos de qualité cinématographique en utilisant des transitions spécialisées (y compris des effets de *Fondu enchaîné, Glissement, Balayage, Zoom et Ken Burns*).
* **Intégration Native avec PhotoKit :** Développé nativement sur **PhotoKit** et **AVFoundation** d'Apple pour prendre en charge une lecture vidéo fluide et haute résolution jusqu'à 60 fps directement sur le matériel iOS et macOS.

---

## 🔒 Engagement de Confidentialité et de Sécurité des Données (Privacy & Data Security Commitment)

Memora a été conçu sous le principe strict de la souveraineté des données de l'utilisateur (Data Sovereignty). Nous garantissons une confidentialité et une sécurité absolues concernant vos photos personnelles.

> [!IMPORTANT]
> * **Zéro Stockage sur Serveur (Zero Server-Side Storage) :** Toute photo transmise à nos serveurs pour la fonction optionnelle "Pro Vision AI" est traitée exclusivement dans la mémoire RAM temporaire. Sous aucun prétexte vos photos ne seront écrites sur disque, enregistrées dans des bases de données, mises en cache ou conservées dans des journaux de serveur.
> * **Entraînement de Modèles d'IA Interdit (No AI Model Training) :** Nous appliquons une politique rigoureuse de non-utilisation pour le développement de l'intelligence artificielle. Vos photos, descriptions générées et métadonnées privées **ne seront jamais** utilisées pour entraîner, ajuster (Fine-Tuning) ou améliorer un grand modèle de langage (LLM), de vision-langage (VLM) ou tout autre modèle d'IA.
> * **Destruction Immédiate de la RAM (Instant RAM Destruction) :** À l'instant même où le serveur proxy répond à votre appareil avec la légende générée, tous les octets de l'image associés dans la RAM sont **immédiatement et définitivement détruits et invalidés**.
> * **Fonctionnement Local par Défaut (On-Device Default) :** Toutes les fonctionnalités fondamentales de l'application (regroupement de photos, indexation locale, reconnaissance faciale et rendu vidéo) s'exécutent à 100 % sur l'appareil local. Sauf si vous choisissez d'activer explicitement Pro Vision AI, aucune photo ne sera jamais transmise via le réseau.

---

## 🛠️ Stack Technique (Technology Stack)

### Client (iOS / macOS)
* **Langage et Frameworks :** Swift 6, SwiftUI, SwiftData, CoreML, Vision, AVFoundation, PhotoKit
* **Écosystème d'IA sur l'Appareil :** `mlx-swift`, `mlx-swift-lm`, `swift-huggingface`, `swift-transformers`
* **Utilitaires de Haute Performance et Réseau :** `yyjson` (analyseur JSON de vitesse extrême), `EventSource` (gestionnaire d'API de streaming SSE), `swift-jinja` (moteur de rendu de modèles)

### Serveur (Proxy Backend en Python)
* **Passerelle d'API et Cœur :** FastAPI, Uvicorn, Starlette, Pydantic et Pydantic Settings
* **Base de Données et Migration :** PostgreSQL, SQLAlchemy (ORM), Alembic, Psycopg 3
* **Cryptographie et Vérification :** `cryptography` (vérification de signatures de l'API Apple App Store), `PyJWT` (traitement de jetons JWS)

---

## ⚖️ Politiques, Conditions et Licences (Policies & Licensing)

Veuillez vous référer aux documents liés suivants pour obtenir des informations exhaustives sur nos politiques légales et licences :

* 📄 **[Politique de Confidentialité (Privacy Policy)](./PRIVACY_POLICY.md)** – Directive détaillée sur la politique de zéro stockage sur serveurs, le stockage local et la synchronisation sécurisée avec iCloud.
* 📄 **[Conditions d'Utilisation (Terms of Service)](./TERMS_OF_SERVICE.md)** – Règles régissant l'utilisation de l'application mobile, les achats intégrés (IAP) via l'Apple App Store et les limites de Pro Vision AI.
* 📄 **[Mentions Légales (Legal Notice)](./LEGAL_NOTICE.md)** – Informations sur le développeur (MFLab-AI / Sang Hun Kim), déclaration de propriété intellectuelle et exclusion de responsabilité.
* 📄 **[Licences Libres (Open Source Licenses)](./OPEN_SOURCE_LICENSES.md)** – Liste détaillée de toutes les bibliothèques de tiers et frameworks open-source intégrés tant dans le client que dans le serveur.

---

## 🛡️ Propriété Intellectuelle et Licence (License)

Copyright (c) 2026 MFLab-AI. Tous droits réservés.

Le code source, les actifs et tous les matériels associés au sein de ce référentiel sont la propriété exclusive de **MFLab-AI**. Ce référentiel est maintenu strictement à des fins informatives, de conformité réglementaire et de démonstration technique. Il est strictement interdit de copier, distribuer, modifier ou utiliser ce logiciel de quelque manière que ce soit sans le consentement écrit préalable de MFLab-AI.
