# Memora (Re-Moment)

🌐 **Select Language / 언어 선택:**
[English](./README.md) | [한국어](./README_KO.md) | [日本語](./README_JA.md) | [简体中文](./README_ZH.md) | [Español](./README_ES.md) | [Français](./README_FR.md) | [Português](./README_PT.md) | [हिन्दी](./README_HI.md) | [বাংলা](./README_BN.md) | [العربية](./README_AR.md)

---

[![Platform: iOS 18+](https://img.shields.io/badge/Platform-iOS%2018%2B-blue.svg?style=flat-square&logo=apple)](https://developer.apple.com/ios/)
[![Platform: macOS 15+](https://img.shields.io/badge/Platform-macOS%2015%2B-lightgrey.svg?style=flat-square&logo=apple)](https://developer.apple.com/macos/)
[![Framework: Swift 6](https://img.shields.io/badge/Framework-Swift%206-orange.svg?style=flat-square&logo=swift)](https://developer.apple.com/swift/)
[![License: Proprietary](https://img.shields.io/badge/License-Proprietary-red.svg?style=flat-square)](./LICENSE)

Memora (cuyo nombre en clave interno es **Re-Moment**) es una aplicación complementaria para historias fotográficas y colecciones inteligentes impulsada por inteligencia artificial local en el dispositivo que prioriza la privacidad. Permite a los usuarios agrupar automáticamente, subtitular de forma hermosa y renderizar dinámicamente presentaciones cinemáticas de sus recuerdos personales, garantizando en todo momento que sus fotos y metadatos permanezcan estrictamente bajo su control exclusivo.

---

## 📸 Funciones Principales (Core Features)

### 🧠 Colecciones Inteligentes Espacio-Temporales
* **Motor de Agrupación y Recomendación:** Agrupa automáticamente los elementos multimedia mediante sofisticados umbrales espaciales (ubicación geográfica) y temporales (intervalos de tiempo) en eventos cohesivos y contextuales (por ejemplo, *"Fin de semana en París"*, *"Picnic de verano"*).
* **Diversificación Temática:** Combina las preferencias del usuario, los metadatos originales de las fotos y las características visuales para generar tarjetas resumen y señales de colecciones estructuradas e inteligentes.

### 🛡️ Inteligencia Artificial de Visión en el Dispositivo (On-Device Vision AI)
* **Indexación de Conocimiento Cero (Zero-Knowledge Indexing):** Realiza el agrupamiento facial primario, la indexación de características y el reconocimiento de objetos por completo en el dispositivo utilizando los marcos de aprendizaje automático locales de Apple (**CoreML**, **Vision** y los ejecutores locales **MLX Swift / MLX Swift LM / MLX VLM**). No se envía ninguna foto fuera del dispositivo.
* **Almacenamiento Local de Metadatos Seguros:** Genera descripciones, subtítulos e historiales que se guardan de forma segura en el espacio aislado (sandbox) del dispositivo o se sincronizan a través de la cuenta personal de **Apple iCloud** del usuario si está activada.

### ⚡ Pro Vision AI (VLM Asistido por la Nube)
* **Subtítulos de Alta Fidelidad:** Función premium opcional que proporciona subtítulos descriptivos enriquecidos y etiquetas detalladas adaptadas al contexto utilizando Modelos de Lenguaje y Visión (VLM) avanzados.
* **Política de Cero Retención en Memoria (In-Memory Zero-Retention Policy):** Las imágenes transmitidas a nuestros servidores se procesan estrictamente en la memoria RAM temporal y se **eliminan al 100 % de manera permanente** de inmediato una vez devuelto el subtítulo generado. No se almacenan fotos, no se registran registros y nunca se usan para entrenamiento de IA.

### 🎬 Renderizado de Presentaciones Cinematográficas de Fotos
* **Motor de Transiciones Dinámicas:** Une automáticamente las fotos de una historia en videos de calidad cinematográfica utilizando transiciones especializadas (incluidos efectos de *Disolución cruzada, Desplazamiento, Barrido, Zoom y Ken Burns*).
* **Integración Nativa con PhotoKit:** Desarrollado de forma nativa sobre **PhotoKit** y **AVFoundation** de Apple para admitir una reproducción de video fluida y de alta resolución de hasta 60 fps directamente en el hardware de iOS y macOS.

---

## 🔒 Compromiso de Privacidad y Seguridad de Datos (Privacy & Data Security Commitment)

Memora ha sido diseñado bajo el estricto principio de la soberanía de los datos del usuario (Data Sovereignty). Garantizamos absoluta confidencialidad y seguridad con respecto a sus fotos personales.

> [!IMPORTANT]
> * **Cero Almacenamiento en el Servidor (Zero Server-Side Storage):** Cualquier foto transmitida a nuestros servidores para la función opcional "Pro Vision AI" se procesa exclusivamente en la memoria RAM temporal. Bajo ninguna circunstancia sus fotos se escribirán en el disco, se guardarán en bases de datos, se almacenarán en caché ni se guardarán en registros del servidor.
> * **Prohibido el Entrenamiento de Modelos de IA (No AI Model Training):** Sostenemos una política rigurosa de cero uso para el desarrollo de inteligencia artificial. Sus fotos, descripciones generadas y metadatos privados **nunca** se utilizarán para entrenar, ajustar (Fine-Tuning) o mejorar ningún modelo de lenguaje grande (LLM), visión-lenguaje (VLM) ni ningún modelo de IA.
> * **Destrucción Inmediata de RAM (Instant RAM Destruction):** En el mismo instante en que el servidor proxy responde a su dispositivo con el subtítulo generado, todos los bytes de la imagen asociados en la RAM se **destruyen e invalidan de inmediato de forma permanente**.
> * **Ejecución Local por Defecto (On-Device Default):** Todas las características fundamentales de la aplicación (agrupamiento de fotos, indexación local, reconocimiento facial y renderizado de video) se ejecutan al 100 % en el dispositivo local. A menos que elija activar Pro Vision AI explícitamente, nunca se transmitirá ninguna foto a través de la red.

---

## 🛠️ Stack Tecnológico (Technology Stack)

### Cliente (iOS / macOS)
* **Lenguaje y Marcos de Trabajo:** Swift 6, SwiftUI, SwiftData, CoreML, Vision, AVFoundation, PhotoKit
* **Ecosistema de IA en el Dispositivo:** `mlx-swift`, `mlx-swift-lm`, `swift-huggingface`, `swift-transformers`
* **Utilidades de Alto Rendimiento y Red:** `yyjson` (analizador JSON de velocidad extrema), `EventSource` (controlador de API de transmisión SSE), `swift-jinja` (renderizador de plantillas)

### Servidor (Proxy Backend en Python)
* **Pasarela de API y Núcleo:** FastAPI, Uvicorn, Starlette, Pydantic y Pydantic Settings
* **Base de Datos y Migración:** PostgreSQL, SQLAlchemy (ORM), Alembic, Psycopg 3
* **Criptografía y Verificación:** `cryptography` (verificación de firmas de la API de Apple App Store), `PyJWT` (procesamiento de tokens JWS)

---

## ⚖️ Políticas, Términos y Licencias (Policies & Licensing)

Consulte los siguientes documentos vinculados para obtener información exhaustiva sobre nuestras políticas legales y licencias:

* 📄 **[Política de Privacidad (Privacy Policy)](./PRIVACY_POLICY.md)** – Directiva detallada sobre la política de cero almacenamiento en servidores, el almacenamiento local y la sincronización segura con iCloud.
* 📄 **[Términos de Servicio (Terms of Service)](./TERMS_OF_SERVICE.md)** – Normas que rigen el uso de la aplicación móvil, compras integradas (IAP) a través de la Apple App Store y límites de Pro Vision AI.
* 📄 **[Aviso Legal (Legal Notice)](./LEGAL_NOTICE.md)** – Información del desarrollador (MFLab-AI / Sang Hun Kim), declaración de propiedad intelectual y exención de responsabilidad.
* 📄 **[Licencias de Código Abierto (Open Source Licenses)](./OPEN_SOURCE_LICENSES.md)** – Lista detallada de todas las bibliotecas de terceros y marcos de código abierto incorporados tanto en el cliente como en el servidor.

---

## 🛡️ Propiedad Intelectual y Licencia (License)

Copyright (c) 2026 MFLab-AI. Reservados todos los derechos.

El código fuente, los activos y todos los materiales asociados dentro de este repositorio son propiedad exclusiva de **MFLab-AI**. Este repositorio se mantiene estrictamente con fines informativos, de cumplimiento normativo y demostraciones técnicas. Queda estrictamente prohibido copiar, distribuir, modificar o utilizar este software de cualquier forma sin el consentimiento previo por escrito de MFLab-AI.
