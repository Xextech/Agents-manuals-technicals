# 03 — Flujo de trabajo, memoria de proyecto y normativa

## 1. Flujo de trabajo de un manual

El sistema funciona por **fases con puertas de aprobación**: el Coordinador no
avanza de fase sin los materiales necesarios y sin el visto bueno del usuario.

### Fase 0 — Alta del proyecto
El Coordinador entrevista al usuario y registra en memoria: producto, tipo de
manual, público objetivo (operario / técnico / instalador), idiomas, formato de
entrega, fecha objetivo. Crea la carpeta de proyecto en SharePoint.

### Fase 1 — Recogida de materiales (checklist)
El Coordinador pide, revisa y marca como recibido cada material:

- [ ] **Plantilla / manual de ejemplo** (estructura y estilo a imitar)
- [ ] **Fotografías e imágenes**: máquina completa, componentes, paneles,
      conexiones, pantallas/interfaz
- [ ] **Inputs de funcionamiento**: especificaciones técnicas, secuencias de
      operación, parámetros, mensajes de error, datos eléctricos/mecánicos
- [ ] **Información de seguridad**: análisis de riesgos, EPIs, condiciones
      ambientales, riesgos residuales
- [ ] **Datos administrativos**: modelo exacto, placa de características,
      contacto de asistencia, declaración UE de conformidad

Si algo falta, el sistema **pregunta de forma proactiva** — este es el
comportamiento clave que pedía el planteamiento original.

### Fase 2 — Escaleta
El Analista de contenido cruza plantilla + materiales y produce la escaleta
(capítulos, contenido asignado, huecos). **El usuario aprueba la escaleta.**

### Fase 3 — Redacción y grafismo (en paralelo)
Redactor técnico escribe capítulo a capítulo; Editor gráfico cataloga imágenes y
define figuras; Seguridad/normativa redacta advertencias y secciones obligatorias.

### Fase 4 — Maquetación
El flujo de maquetación compone el Word con la plantilla corporativa e inserta
las figuras. Salida: borrador maquetado en `/borradores`.

### Fase 5 — QA y entrega
QA pasa los checklists (normativo + estilo). Con el visto bueno del usuario, el
documento pasa a `/versiones` como **vX.Y** con su registro de cambios, y el
Coordinador archiva en memoria las decisiones del proyecto.

### Modificaciones y nuevas versiones
Para una revisión, el Coordinador recupera de la memoria el contexto del manual
(decisiones, glosario, versión vigente), aplica solo los cambios pedidos y genera
la versión siguiente con su historial. Así el equipo "no se pierde la
información" entre proyectos y versiones.

## 2. Sistema de memoria (equivalente al de Neuroforge)

Dos capas complementarias:

### Capa documental — SharePoint
```
Manuales Técnicos/
├── _plantillas/            ← plantillas corporativas y manuales de ejemplo
├── _glosario/              ← glosario general Azkoyen
└── <Producto>/<Manual>/
    ├── materiales/         ← fotos, specs, inputs entregados
    ├── borradores/
    ├── versiones/          ← v1.0.docx/pdf, v1.1..., con registro de cambios
    └── memoria-proyecto.md ← decisiones, criterios, pendientes
```

### Capa estructurada — Dataverse (o listas SharePoint si no hay Dataverse)

| Tabla | Campos clave | Para qué |
|---|---|---|
| `Proyecto` | producto, tipo de manual, idiomas, estado, fase | Saber en qué punto está cada manual |
| `DecisiónEditorial` | proyecto, fecha, decisión, motivo | "Aprendizaje" reutilizable en versiones futuras |
| `VersiónManual` | proyecto, versión, fecha, cambios, ruta al archivo | Historial y trazabilidad (la normativa exige disponibilidad ~10 años) |
| `TérminoGlosario` | término, definición, traducciones, familia de producto | Coherencia terminológica entre manuales |

Los agentes usan estas tablas como conocimiento: al abrir un proyecto existente,
el Coordinador carga sus decisiones y glosario antes de trabajar.

## 3. Normativa aplicable (lo que el agente de Seguridad debe garantizar)

- **Reglamento (UE) 2023/1230 de máquinas** — sustituye a la Directiva 2006/42/CE
  y es de plena aplicación en **enero de 2027**: el piloto debe nacer ya conforme
  a él. Novedades relevantes: se permite el **manual en formato digital**, pero
  debe ser **imprimible** y estar **accesible en línea durante la vida útil de la
  máquina y como mínimo 10 años** tras su comercialización.
- **EN ISO 20607** — contenido de seguridad del manual de instrucciones de
  maquinaria (estructura mínima, riesgos residuales, uso previsto e indebido).
- **IEC/IEEE 82079-1:2019** — principios generales de preparación de información
  de uso (aplica a todo producto; es la norma "editorial" de referencia).
- **ISO 3864 / ISO 7010** — colores y símbolos de seguridad para advertencias.
- (Si se exporta a EE. UU.: **ANSI Z535.6** para el formato de advertencias.)

### Checklist normativo mínimo del QA
1. Identificación del fabricante y de la máquina (modelo, serie, placa).
2. Declaración UE de conformidad (o referencia a ella).
3. Uso previsto **y** usos indebidos razonablemente previsibles.
4. Instrucciones de instalación, puesta en servicio, uso, mantenimiento y limpieza.
5. Advertencias de riesgos residuales con gradación y símbolos correctos.
6. EPIs requeridos y cualificación del personal.
7. Datos técnicos (eléctricos, ruido, condiciones ambientales).
8. Instrucciones de transporte, almacenamiento y puesta fuera de servicio/reciclaje.
9. Índices, numeración de figuras y referencias cruzadas correctos.
10. Versión, fecha e historial de revisiones en el propio documento.
