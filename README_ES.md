# Memora (Re-Moment)

Seleccionar idioma:
[English](./README.md) | [한국어](./README_KO.md) | [日本語](./README_JA.md) | [简体中文](./README_ZH.md) | [Español](./README_ES.md) | [Français](./README_FR.md) | [Português](./README_PT.md) | [हिन्दी](./README_HI.md) | [বাংলা](./README_BN.md) | [العربية](./README_AR.md)

---

[![Platform: iOS 18+](https://img.shields.io/badge/Platform-iOS%2018%2B-blue.svg?style=flat-square&logo=apple)](https://developer.apple.com/ios/)
[![Platform: iPadOS 18+](https://img.shields.io/badge/Platform-iPadOS%2018%2B-blue.svg?style=flat-square&logo=apple)](https://developer.apple.com/ipados/)
[![Framework: Swift 6](https://img.shields.io/badge/Framework-Swift%206-orange.svg?style=flat-square&logo=swift)](https://developer.apple.com/swift/)
[![License: Proprietary](https://img.shields.io/badge/License-Proprietary-red.svg?style=flat-square)](./LICENSE.md)

Memora, con nombre interno **Re-Moment**, es una app para iPhone y iPad con enfoque local-first que analiza la biblioteca de Fotos del usuario y convierte momentos relacionados en videos cortos de recuerdos. La app se centra en indexación privada de fotos, recomendaciones revisables, borradores de historias editables y renderizado en el dispositivo. Pro Vision AI es una opción de pago para subtítulos de mayor calidad e indexación asistida remotamente.

---

## Funciones principales

### Recomendaciones inteligentes de historias
* **Indexación de la biblioteca de fotos:** Memora lee las fotos permitidas por el usuario con PhotoKit y extrae señales de fecha, ubicación, favoritos, tipo de medio, calidad, conteo de rostros, escena y subtítulos.
* **Tarjetas de recomendación:** La app crea candidatos de historias como momentos con la misma persona, fondos similares, comidas, recuerdos estacionales, ciudad/viaje, instantáneas temporales, momentos significativos y destacados de video.
* **Búsqueda y mantenimiento:** Las fotos indexadas se pueden buscar localmente. También hay acciones para completar traducciones, reparar coherencia, reiniciar comentarios de recomendación y ayudar a reanudar la indexación.

### Historias de recuerdos revisables
* **Revisión de historias:** Antes de renderizar, los usuarios pueden revisar una historia sugerida, reemplazar o quitar fotos, agregar más candidatos, reordenar recursos y registrar personas representativas desde fotos con rostros claros.
* **Controles de feedback:** Los usuarios pueden archivar historias generadas, ocultar una recomendación específica, ocultar tipos similares de recomendación y deshacer comentarios recientes.
* **Soporte de personas:** Los perfiles de personas registrados pueden usarse para crear historias centradas en personas y mejorar recomendaciones futuras.

### Vision y almacenamiento local-first
* **Predeterminado en el dispositivo:** La indexación estándar y los subtítulos de respaldo usan PhotoKit, Vision y análisis de metadatos locales. Las fotos no se envían al servidor salvo que el usuario active y use Pro Vision AI.
* **Base de datos local:** Memora guarda índices, historias, trabajos de renderizado, preferencias, puntos de control y perfiles de personas en el sandbox de la app con SwiftData. Donde esté disponible, el usuario puede elegir almacenamiento de base de datos con iCloud Drive.
* **Diagnósticos:** MetricKit se usa para investigar bloqueos, cuelgues, arranque, CPU y problemas de escritura en disco. Estos diagnósticos no incluyen archivos de fotos del usuario.

### Pro Vision AI
* **Función opcional de pago:** Pro Vision AI usa un proxy del servidor para subtítulos VLM mejorados y control de cuota de indexación remota. Si no hay cuota o el servidor no está disponible, la app sigue funcionando con Vision AI local estándar.
* **Control del servidor:** El backend verifica el estado de derechos de StoreKit, emite tokens de acceso de corta duración, aplica cuotas, protege claves API del proveedor, gestiona idempotencia y registra señales contra abusos.
* **Manejo de imágenes:** Las cargas de imagen se reenvían solo para la operación de subtitulado solicitada. El servicio está diseñado para no almacenar bytes originales de imagen para uso del producto ni entrenamiento de IA. Pueden conservarse registros operativos como metadatos sanitizados de solicitud, texto de respuesta del proveedor, estado de solicitud, contadores de cuota, hashes de dispositivo e información de errores para derechos, cuotas, depuración, seguridad y prevención de abuso.

### Renderizado y guardado de video
* **Renderizador nativo:** Las historias se renderizan con AVFoundation desde recursos de foto en caché, con objetivo predeterminado de 30fps y efectos de movimiento/transición como dissolve, slide, wipe y zoom.
* **Exportación a Fotos:** Antes de renderizar, Memora prepara copias locales de recursos solo en iCloud cuando es necesario. Los videos renderizados se guardan en Fotos con permiso add-only y fallback MOV compatible.
* **Progreso y cancelación:** La app muestra estados de descarga, renderizado, guardado, fallo, cancelación y recuperación.

---

## Notas importantes

* Memora requiere acceso de lectura a Fotos para indexar y recomendar historias. El acceso limitado está soportado, pero el acceso completo ofrece la experiencia prevista.
* Guardar videos renderizados requiere permiso de agregar a Fotos.
* Pro Vision AI envía datos de imagen seleccionados al backend y al proveedor VLM configurado. Úsalo solo con fotos que aceptes procesar remotamente.
* Los subtítulos y recomendaciones generados por IA pueden ser inexactos. Revisa el contenido antes de renderizarlo o compartirlo.
* El almacenamiento con iCloud Drive depende de la configuración de Apple iCloud y disponibilidad del dispositivo.
* Los nombres de producto, cuotas, precios y disponibilidad de plataformas pueden cambiar antes o después del lanzamiento en App Store.

---

## Stack tecnológico

### Cliente
* Swift 6, SwiftUI, SwiftData
* PhotoKit, Vision, AVFoundation, MetricKit
* Paquetes relacionados con MLX Swift LM / MLX VLM, Swift HuggingFace, Swift Transformers

### Servidor
* FastAPI, Uvicorn, Starlette
* PostgreSQL, SQLAlchemy, Alembic, Psycopg 3
* Pydantic, Pydantic Settings, HTTPX
* PyJWT y cryptography para rutas de verificación de StoreKit y tokens

---

## Políticas y licencias

* [Privacy Policy](./PRIVACY_POLICY.md)
* [Terms of Service](./TERMS_OF_SERVICE.md)
* [Legal Notice](./LEGAL_NOTICE.md)
* [Open Source Licenses](./OPEN_SOURCE_LICENSES.md)
* [Proprietary License](./LICENSE.md)

---

## Licencia

Copyright (c) 2026 MFLab-AI. All rights reserved.

El código fuente, recursos, marca, documentación y materiales relacionados de Memora son propietarios salvo que exista una licencia escrita separada. Los componentes open-source de terceros se rigen por sus propias licencias.
