# Open Source Licenses

Memora uses third-party open-source software in the client and server. This page is a summary for notice purposes and does not replace the full license texts from each project.

## Client

- **MLX Swift / MLX Swift LM / MLX VLM-related packages**: MIT License
- **Swift HuggingFace**: Apache License 2.0
- **Swift Transformers / Tokenizers**: Apache License 2.0
- **Apple Swift packages pulled transitively by Swift Package Manager**: governed by their respective package licenses

## Server

- **FastAPI**: MIT License
- **Uvicorn**: BSD 3-Clause License
- **Starlette**: BSD 3-Clause License
- **Pydantic / Pydantic Settings**: MIT License
- **SQLAlchemy / Alembic**: MIT License
- **Psycopg 3**: LGPL 3.0 or project-specific distribution terms
- **HTTPX**: BSD 3-Clause License
- **PyJWT**: MIT License
- **cryptography**: Apache License 2.0 and BSD 3-Clause License
- **python-multipart**: Apache License 2.0

## Notes

Some dependencies may include their own transitive dependencies and notices. When distributing the App or server artifacts, include the complete third-party license texts generated from the locked dependency set used for that release.
