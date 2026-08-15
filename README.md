# Ecosistema de Automatización IA Autónomo para Negocios

Pipeline autónomo end-to-end construido en n8n que genera contenido con RAG, pasa por un punto de validación humana (HITL) en Airtable, y publica automáticamente al ser aprobado.

## Arquitectura

- **Orquestador:** n8n (Flujo A: Generación → Flujo B: Aprobación → Publicado)
- **Base de datos / control:** Airtable (tablas Contenidos y Errores)
- **Procesamiento IA:** OpenAI GPT-5-mini con RAG (directrices desde Airtable)
- **Canal de salida:** Gmail (notificación intermedia para validación humana)

Ver diagrama completo en [`docs/entrega-final.pdf`](docs/entrega-final.pdf).

## Flujo de trabajo

1. **Flujo A – Generación:** se dispara con una Idea Semilla lista, valida datos, busca directrices RAG en Airtable, y genera el contenido con IA.
2. **HITL:** el borrador se guarda con Estado = "Pendiente Aprobación" y se notifica por Gmail al humano responsable.
3. **Validación humana:** el humano revisa y tilda "Aprobado" en Airtable.
4. **Flujo B – Publicación:** detecta el registro aprobado y actualiza el Estado a "Publicado".

## Manejo de errores

Rutas de error dedicadas ante datos faltantes o fallos de API, registradas en la tabla Errores de Airtable.

## Evidencia y demo

- 🎥 **Video demo (Loom):** https://www.loom.com/share/f870c51d92524349973502720de92d36
- 📊 **Dashboard Contenidos (Airtable):** https://airtable.com/app7aBgH53gjQv5EC/shrIW3YmF7ce7yHTP
- 📊 **Dashboard Errores (Airtable):** https://airtable.com/app7aBgH53gjQv5EC/shrnZOEao70bHVLxC
- 📄 **Documentación completa (PDF):** [`docs/entrega-final.pdf`](docs/entrega-final.pdf)

## Contenido del repositorio
── docs/
│ └── entrega-final.pdf # Diagrama de arquitectura, esquemas, costos, seguridad
├── workflows/
│ ├── flujo-a-generacion.json
│ └── flujo-b-aprobacion-publicado.json
└── screenshots/ # Capturas de evidencia
---
Proyecto final — Curso IA Automation, Coderhouse.
