# Memora (Re-Moment)

Selecionar idioma:
[English](./README.md) | [한국어](./README_KO.md) | [日本語](./README_JA.md) | [简体中文](./README_ZH.md) | [Español](./README_ES.md) | [Français](./README_FR.md) | [Português](./README_PT.md) | [हिन्दी](./README_HI.md) | [বাংলা](./README_BN.md) | [العربية](./README_AR.md)

---

[![Platform: iOS 18+](https://img.shields.io/badge/Platform-iOS%2018%2B-blue.svg?style=flat-square&logo=apple)](https://developer.apple.com/ios/)
[![Platform: iPadOS 18+](https://img.shields.io/badge/Platform-iPadOS%2018%2B-blue.svg?style=flat-square&logo=apple)](https://developer.apple.com/ipados/)
[![Framework: Swift 6](https://img.shields.io/badge/Framework-Swift%206-orange.svg?style=flat-square&logo=swift)](https://developer.apple.com/swift/)
[![License: Proprietary](https://img.shields.io/badge/License-Proprietary-red.svg?style=flat-square)](./LICENSE.md)

Memora, codinome interno **Re-Moment**, e um app para iPhone e iPad com abordagem local-first que analisa a biblioteca de Fotos do usuario e transforma momentos relacionados em videos curtos de memoria. O app foca em indexacao privada de fotos, recomendacoes revisaveis, rascunhos de historias editaveis e renderizacao no dispositivo. Pro Vision AI e uma opcao paga para legendas de maior qualidade e indexacao assistida remotamente.

---

## Principais recursos

### Recomendacoes inteligentes de historias
* **Indexacao da biblioteca de fotos:** Memora le as fotos permitidas pelo usuario com PhotoKit e extrai sinais de data, local, favorito, tipo de midia, qualidade, contagem de rostos, cena e legenda.
* **Cartoes de recomendacao:** O app cria candidatos de historias como mesma pessoa, fundos semelhantes, comida, memorias sazonais, cidade/viagem, instantaneos temporais, momentos significativos e destaques de video.
* **Busca e manutencao:** Fotos indexadas podem ser pesquisadas localmente. O app tambem inclui complemento de traducao, reparo de consistencia, redefinicao de feedback de recomendacao e auxilio para retomar indexacao.

### Historias de memoria revisaveis
* **Revisao de historia:** Antes de renderizar, usuarios podem revisar uma historia sugerida, substituir ou remover fotos, adicionar candidatos, reordenar itens e registrar pessoas representativas a partir de fotos com rostos claros.
* **Controles de feedback:** Usuarios podem arquivar historias geradas, ocultar uma recomendacao especifica, ocultar tipos semelhantes e desfazer feedback recente.
* **Suporte a pessoas:** Perfis de pessoas registrados podem ser usados para criar historias centradas em pessoas e melhorar recomendacoes futuras.

### Vision e armazenamento local-first
* **Padrao no dispositivo:** A indexacao padrao e legendas de fallback usam PhotoKit, Vision e analise de metadados locais. Fotos nao sao enviadas ao servidor salvo quando o usuario ativa e usa Pro Vision AI.
* **Banco local:** Memora armazena indices, historias, trabalhos de renderizacao, preferencias, checkpoints e perfis de pessoas no sandbox do app com SwiftData. Quando disponivel, o usuario pode escolher armazenamento de banco via iCloud Drive.
* **Diagnosticos:** MetricKit e usado para investigar crashes, travamentos, inicializacao, CPU e problemas de escrita em disco. Esses diagnosticos nao incluem arquivos de fotos do usuario.

### Pro Vision AI
* **Recurso pago opcional:** Pro Vision AI usa um proxy no servidor para legendas VLM aprimoradas e controle de cota de indexacao remota. Quando a cota acaba ou o servidor nao pode ser acessado, o app continua utilizavel com Vision AI local padrao.
* **Controle no servidor:** O backend verifica direitos StoreKit, emite tokens de curta duracao, aplica cotas, protege chaves API do provedor, trata idempotencia e acompanha sinais contra abuso.
* **Tratamento de imagens:** Dados de imagem sao encaminhados apenas para a operacao de legenda solicitada. O servico e projetado para nao armazenar bytes originais de imagem para uso do produto ou treinamento de IA. Registros operacionais como metadados sanitizados de requisicao, texto de resposta do provedor, status da requisicao, contadores de cota, hashes de dispositivo e erros podem ser retidos para direitos, cota, depuracao, seguranca e prevencao de abuso.

### Renderizacao e salvamento de video
* **Renderizador nativo:** Historias sao renderizadas com AVFoundation a partir de fotos em cache, com alvo padrao de 30fps e efeitos como dissolve, slide, wipe e zoom.
* **Exportacao para Fotos:** Antes da renderizacao, Memora prepara copias locais de itens iCloud-only quando necessario. Videos renderizados sao salvos no Fotos com permissao add-only e fallback MOV compativel.
* **Progresso e cancelamento:** O app mostra estados de download, renderizacao, salvamento, falha, cancelamento e recuperacao.

---

## Observacoes importantes

* Memora requer acesso de leitura ao Fotos para indexar e recomendar historias. Acesso limitado e suportado, mas acesso completo oferece a experiencia pretendida.
* Salvar videos renderizados exige permissao para adicionar ao Fotos.
* Pro Vision AI envia dados de imagem selecionados ao backend e ao provedor VLM configurado. Use apenas com fotos que voce aceita processar remotamente.
* Legendas e recomendacoes geradas por IA podem ser imprecisas. Revise o conteudo antes de renderizar ou compartilhar.
* Armazenamento via iCloud Drive depende da configuracao Apple iCloud e disponibilidade do dispositivo.
* Nomes de produto, cotas, precos e plataformas suportadas podem mudar antes ou depois do lancamento na App Store.

---

## Stack tecnologico

### Cliente
* Swift 6, SwiftUI, SwiftData
* PhotoKit, Vision, AVFoundation, MetricKit
* Pacotes relacionados a MLX Swift LM / MLX VLM, Swift HuggingFace, Swift Transformers

### Servidor
* FastAPI, Uvicorn, Starlette
* PostgreSQL, SQLAlchemy, Alembic, Psycopg 3
* Pydantic, Pydantic Settings, HTTPX
* PyJWT e cryptography para verificacao StoreKit e tokens

---

## Politicas e licencas

* [Privacy Policy](./PRIVACY_POLICY.md)
* [Terms of Service](./TERMS_OF_SERVICE.md)
* [Legal Notice](./LEGAL_NOTICE.md)
* [Open Source Licenses](./OPEN_SOURCE_LICENSES.md)
* [Proprietary License](./LICENSE.md)

---

## Licenca

Copyright (c) 2026 MFLab-AI. All rights reserved.

O codigo-fonte, ativos, marca, documentacao e materiais relacionados da Memora sao proprietarios salvo licenca escrita separada. Componentes open-source de terceiros seguem suas proprias licencas.
