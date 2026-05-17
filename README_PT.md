# Memora (Re-Moment)

🌐 **Select Language / 언어 선택:**
[English](./README.md) | [한국어](./README_KO.md) | [日本語](./README_JA.md) | [简体中文](./README_ZH.md) | [Español](./README_ES.md) | [Français](./README_FR.md) | [Português](./README_PT.md) | [हिन्दी](./README_HI.md) | [বাংলা](./README_BN.md) | [العربية](./README_AR.md)

---

[![Platform: iOS 18+](https://img.shields.io/badge/Platform-iOS%2018%2B-blue.svg?style=flat-square&logo=apple)](https://developer.apple.com/ios/)
[![Platform: macOS 15+](https://img.shields.io/badge/Platform-macOS%2015%2B-lightgrey.svg?style=flat-square&logo=apple)](https://developer.apple.com/macos/)
[![Framework: Swift 6](https://img.shields.io/badge/Framework-Swift%206-orange.svg?style=flat-square&logo=swift)](https://developer.apple.com/swift/)
[![License: Proprietary](https://img.shields.io/badge/License-Proprietary-red.svg?style=flat-square)](./LICENSE)

Memora (cujo codinome interno é **Re-Moment**) é um aplicativo complementar para narrativas fotográficas e coleções inteligentes alimentado por inteligência artificial local no dispositivo que prioriza a privacidade. Ele permite que os usuários agrupem automaticamente, criem belas legendas narrativas e renderizem dinamicamente apresentações cinematográficas de suas memórias pessoais—tudo isso enquanto garante que suas fotos e metadados permaneçam estritamente sob seu próprio controle exclusivo.

---

## 📸 Recursos Principais (Core Features)

### 🧠 Coleções Inteligentes Espaço-Temporais
* **Motor de Agrupamento e Recomendação:** Agrupa automaticamente os arquivos de mídia por meio de sofisticados limites espaciais (localização geográfica) e temporais (intervalos de tempo) em eventos coesos e contextuais (por exemplo, *"Fim de semana em Paris"*, *"Picnic de verão"*).
* **Diversificação Temática:** Combina as preferências do usuário, metadatos originais das fotos e características visuais para gerar cartões de resumo e sinais de coleções inteligentes e estruturados.

### 🛡️ Inteligência Artificial de Visão no Dispositivo (On-Device Vision AI)
* **Indexação de Conhecimento Zero (Zero-Knowledge Indexing):** Realiza o agrupamento facial primário, indexação de características e reconhecimento de objetos inteiramente no dispositivo usando as estruturas de aprendizado de máquina locais da Apple (**CoreML**, **Vision** e os executores locais **MLX Swift / MLX Swift LM / MLX VLM**). Nenhuma foto sai do dispositivo.
* **Armazenamento Local de Metadados Seguros:** Gera descrições, legendas e históricos salvos com segurança no sandbox do dispositivo ou sincronizados por meio da conta pessoal do **Apple iCloud** do usuário, se ativada.

### ⚡ Pro Vision AI (VLM Assistido pela Nuvem)
* **Legendas de Alta Fidelidade:** Recurso premium opcional que fornece legendas ricas e detalhadas e tags adaptadas ao contexto usando Modelos de Linguagem e Visão (VLM) avançados.
* **Política de Zero Retenção na Memória (In-Memory Zero-Retention Policy):** As imagens transmitidas aos nossos servidores são processadas estritamente na memória RAM temporária e são **excluídas a 100% de forma permanente** imediatamente após o retorno da legenda gerada. Nenhuma foto é armazenada, nenhum registro é salvo e elas nunca são usadas para treinamento de IA.

### 🎬 Renderização de Apresentações Cinematográficas de Fotos
* **Motor de Transições Dinâmicas:** Une automaticamente as fotos de uma história em vídeos de qualidade cinematográfica usando transições especializadas (incluindo efeitos de *Dissolução cruzada, Deslocamento, Varredura, Zoom e Ken Burns*).
* **Integração Nativa com o PhotoKit:** Desenvolvido nativamente sobre o **PhotoKit** e o **AVFoundation** da Apple para oferecer suporte a uma reprodução de vídeo fluida e de alta resolução de até 60 fps diretamente no hardware do iOS e macOS.

---

## 🔒 Compromisso de Privacidade e Segurança de Dados (Privacy & Data Security Commitment)

O Memora foi projetado sob o princípio estrito da soberania dos dados do usuário (Data Sovereignty). Garantimos absoluta confidencialidade e segurança em relação às suas fotos pessoais.

> [!IMPORTANT]
> * **Zero Armazenamento no Servidor (Zero Server-Side Storage):** Qualquer foto transmitida aos nossos servidores para o recurso opcional "Pro Vision AI" é processada exclusivamente na memória RAM temporária. Sob nenhuma circunstância suas fotos serão gravadas no disco, salvas em bancos de dados, armazenadas em cache ou mantidas em registros de servidor.
> * **Proibido o Treinamento de Modelos de IA (No AI Model Training):** Mantemos uma política rigorosa de não utilização para o desenvolvimento de inteligência artificial. Suas fotos, descrições geradas e metadatos privados **nunca** serão usados para treinar, ajustar (Fine-Tuning) ou melhorar qualquer modelo de linguagem grande (LLM), visão-linguagem (VLM) ou qualquer modelo de IA.
> * **Destruição Imediata da RAM (Instant RAM Destruction):** No exato instante em que o servidor proxy responde ao seu dispositivo com a legenda gerada, todos os bytes de imagem associados na RAM são **destruídos e invalidados de forma permanente de imediato**.
> * **Execução Local por Padrão (On-Device Default):** Todos os recursos fundamentais da aplicação (agrupamento de fotos, indexação local, reconhecimento facial e renderização de vídeo) são executados 100% no dispositivo local. A menos que escolha ativar o Pro Vision AI explicitamente, nenhuma foto será transmitida através da rede.

---

## 🛠️ Stack Tecnológico (Technology Stack)

### Cliente (iOS / macOS)
* **Linguagem e Frameworks:** Swift 6, SwiftUI, SwiftData, CoreML, Vision, AVFoundation, PhotoKit
* **Ecossistema de IA no Dispositivo:** `mlx-swift`, `mlx-swift-lm`, `swift-huggingface`, `swift-transformers`
* **Utilitários de Alto Desempenho e Rede:** `yyjson` (analisador JSON de velocidade extrema), `EventSource` (controlador de API de transmissão SSE), `swift-jinja` (renderizador de modelos)

### Servidor (Proxy Backend em Python)
* **Gateway de API e Núcleo:** FastAPI, Uvicorn, Starlette, Pydantic e Pydantic Settings
* **Banco de Dados e Migração:** PostgreSQL, SQLAlchemy (ORM), Alembic, Psycopg 3
* **Criptografia e Verificação:** `cryptography` (verificação de assinaturas da API da Apple App Store), `PyJWT` (processamento de tokens JWS)

---

## ⚖️ Políticas, Termos e Licenciamento (Policies & Licensing)

Consulte os seguintes documentos vinculados para obter informações abrangentes sobre nossas políticas legais e licenças:

* 📄 **[Política de Privacidade (Privacy Policy)](./PRIVACY_POLICY.md)** – Diretriz detalhada sobre a política de zero armazenamento em servidores, armazenamento local e sincronização segura com o iCloud.
* 📄 **[Termos de Serviço (Terms of Service)](./TERMS_OF_SERVICE.md)** – Normas que regem o uso do aplicativo móvel, compras integradas (IAP) através da Apple App Store e limites de Pro Vision AI.
* 📄 **[Aviso Legal (Legal Notice)](./LEGAL_NOTICE.md)** – Informações do desenvolvedor (MFLab-AI / Sang Hun Kim), declaração de propriedade intelectual e isenção de responsabilidade.
* 📄 **[Licenças de Código Aberto (Open Source Licenses)](./OPEN_SOURCE_LICENSES.md)** – Lista detalhada de todas as bibliotecas de terceiros e frameworks de código aberto incorporados tanto no cliente quanto no servidor.

---

## 🛡️ Propriedade Intelectual e Licença (License)

Copyright (c) 2026 MFLab-AI. Todos os direitos reservados.

O código fonte, os ativos e todos os materiais associados dentro deste repositório são de propriedade exclusiva da **MFLab-AI**. Este repositório é mantido estritamente para fins informativos, conformidade regulatória e demonstração técnica. É estritamente proibido copiar, distribuir, modificar ou utilizar este software de qualquer forma sem o consentimento prévio por escrito da MFLab-AI.
