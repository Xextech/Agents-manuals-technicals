# Equipo de Agentes — Edición de Manuales Técnicos (Azkoyen)

Sistema de agentes tipo "equipo editorial" para diseñar, maquetar y editar manuales
técnicos de productos industriales de Azkoyen (vending, café, medios de pago),
siguiendo el mismo planteamiento de equipo multi-agente con memoria que el proyecto
Neuroforge, pero orientado a documentación técnica en lugar de programación.

**Restricción de plataforma:** el sistema debe funcionar dentro del entorno Microsoft
(Microsoft 365 Copilot / Copilot Studio), que es donde la empresa tiene garantizada
la privacidad de los datos.

## Documentación

| Documento | Contenido |
|---|---|
| [docs/01-equipo-editorial.md](docs/01-equipo-editorial.md) | Investigación: roles de un equipo profesional de edición de manuales técnicos y su traducción a subagentes |
| [docs/02-arquitectura-microsoft.md](docs/02-arquitectura-microsoft.md) | Opciones de arquitectura en el ecosistema Microsoft y recomendación (¿aplicación u orquestador con subagentes?) |
| [docs/03-flujo-memoria-normativa.md](docs/03-flujo-memoria-normativa.md) | Flujo de trabajo del manual, sistema de memoria por proyecto y requisitos normativos (Reglamento UE 2023/1230, ISO 20607, IEC/IEEE 82079-1) |
| [docs/04-alternativa-claude.md](docs/04-alternativa-claude.md) | Alternativa con Claude: protección de datos empresariales (Enterprise, API, Claude en Microsoft Foundry) y planteamiento nativo estilo Neuroforge |

## Estado

Fase de propuesta: pendiente de validar el plan con el equipo antes de construir
los agentes en Copilot Studio. Las preguntas abiertas están al final del
documento 02.
