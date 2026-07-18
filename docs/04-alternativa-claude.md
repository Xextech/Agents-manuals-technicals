# 04 — Alternativa con Claude: planteamiento y protección de datos

Respuesta a dos preguntas: ¿cómo sería el equipo si lo montamos con Claude?
¿Existe una versión de Claude que proteja los datos de empresa como Copilot?

## 1. Protección de datos: sí, por tres vías

### a) Claude Team / Enterprise (Anthropic directo)
- Anthropic **no entrena sus modelos con los datos de ningún plan de pago
  empresarial** (Team, Enterprise, API): mismo principio que Microsoft con Copilot.
- El plan **Enterprise** añade lo que exige IT: SSO SAML/SCIM (compatible con
  Entra ID), logs de auditoría, API de cumplimiento (integrable con SIEM/DLP),
  retención personalizada, control de acceso por roles y opciones de residencia
  de datos. Certificaciones: SOC 2 Type II, ISO 27001:2022 e ISO/IEC 42001:2023
  (gestión de IA), y RGPD.

### b) Claude API (para una aplicación a medida)
- Igual: sin entrenamiento con datos del cliente por defecto, con contrato
  empresarial y DPA.

### c) Claude dentro del propio paraguas Microsoft ⭐ (la vía más interesante para Azkoyen)
Desde la alianza Anthropic–Microsoft (nov. 2025), y con **disponibilidad general
en junio de 2026**, los modelos Claude:
- Están **hospedados en Azure vía Microsoft Foundry**: los datos se procesan
  dentro de la gobernanza Azure del propio tenant, con los controles Microsoft
  que ya tenemos contratados.
- Se pueden **elegir como modelo en Copilot Studio** para agentes personalizados,
  y ya impulsan funciones de M365 Copilot (agente Researcher, modo agente de Excel).

**Conclusión clave:** la restricción "tiene que funcionar desde Microsoft" ya no
excluye a Claude. Podemos mantener la arquitectura del doc 02 (orquestador +
subagentes en Copilot Studio, SharePoint + Dataverse) y **seleccionar Claude como
motor de los agentes** — privacidad Microsoft con cerebro Claude.

## 2. Planteamiento 100 % Claude (estilo Neuroforge)

Si se montara nativo en Claude (Claude Code / Agent SDK, como Neuroforge):

- **Equipo**: los mismos 7 roles del doc 01, definidos como subagentes en
  `.claude/agents/*.md` de este repositorio. El Coordinador es la sesión
  principal; delega en redactor, analista, seguridad, gráfico, QA.
- **Memoria**: `CLAUDE.md` + carpeta `memoria/` por proyecto en el repo
  (decisiones, glosario, historial de versiones), versionada en git — exactamente
  el esquema de Neuroforge, sin necesidad de Dataverse.
- **Materiales**: carpeta `proyectos/<producto>/<manual>/materiales/` con las
  fotos, la plantilla de ejemplo y los inputs de funcionamiento. Si los
  materiales viven en SharePoint, se conecta vía MCP/conectores.
- **Maquetación**: Claude Code genera directamente el **Word y el PDF finales**
  con sus skills nativas de documentos (docx/pdf), sin Power Automate.

### Ventajas del planteamiento Claude nativo
1. **Visión multimodal real**: el Editor gráfico *ve* las fotografías (encuadre,
   calidad, qué componente aparece) y puede proponer callouts con criterio. En
   Copilot Studio el tratamiento de imágenes es mucho más limitado.
2. **Subagentes más profundos**: contextos largos, razonamiento extenso,
   iteración fina de cada capítulo.
3. **Todo versionado en git**: instrucciones, memoria y entregas en un solo sitio.
4. **Sin coste por mensaje** de Copilot Studio (se paga plan/API de Claude).

### Inconvenientes
1. Interfaz: Claude Code / claude.ai en vez del Copilot integrado en Teams/Office
   que el equipo ya usa a diario.
2. Un segundo proveedor con contrato y gobernanza propios (aunque con garantías
   equivalentes, apartado 1a).
3. Los materiales hay que traerlos al entorno Claude (repo o conectores),
   mientras que Copilot Studio ya vive sobre SharePoint.

## 3. Comparativa y recomendación

| Criterio | Copilot Studio (modelo MS) | Copilot Studio + **modelo Claude** | Claude nativo (Code/SDK) |
|---|---|---|---|
| Privacidad bajo tenant Microsoft | ✅ | ✅ (Claude hospedado en Azure/Foundry) | ⚠️ Garantías Anthropic (equivalentes, otro contrato) |
| Integración día a día (Teams/Office) | ✅ | ✅ | ❌ Herramienta aparte |
| Calidad de redacción y razonamiento | Media | **Alta** | **Alta** |
| Tratamiento de imágenes/fotos | Limitado | Limitado (por la plataforma) | **Excelente** |
| Maquetación Word/PDF | Vía Power Automate | Vía Power Automate | **Nativa** |
| Memoria por proyecto | Dataverse/SharePoint | Dataverse/SharePoint | Git + archivos (estilo Neuroforge) |
| Coste | Licencias CS | Licencias CS | Plan Claude / API |

**Recomendación actualizada:**
- **Camino principal:** mantener la arquitectura del doc 02 pero con **modelos
  Claude seleccionados en Copilot Studio** — cumple la restricción de privacidad
  Microsoft y mejora la calidad editorial sin cambiar de plataforma.
- **Camino de prototipado:** montar primero el equipo completo en **Claude Code
  sobre este repo** (barato y rápido, como Neuroforge) para afinar roles,
  instrucciones, checklists y flujo con un manual piloto real; después portar las
  instrucciones afinadas a Copilot Studio.
- Si a futuro Copilot Studio se queda corto (sobre todo en imágenes y
  maquetación), la Opción C del doc 02 se construiría como *custom engine agent*
  con **Claude en Microsoft Foundry** como motor: aplicación propia, pero datos
  siempre en Azure.
