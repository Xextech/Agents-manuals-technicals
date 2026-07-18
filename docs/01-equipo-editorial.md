# 01 — El equipo editorial: roles y subagentes

Investigación sobre cómo se compone una empresa/departamento profesional de edición
de manuales técnicos de maquinaria industrial, y cómo se traduce cada rol a un
subagente de nuestro sistema.

## 1. Cómo trabaja una editorial técnica real

En el sector de la documentación técnica industrial (tekom, empresas de technical
publications) el trabajo se reparte siempre entre los mismos perfiles: un gestor de
proyecto editorial coordina; un redactor técnico escribe a partir de la información
de ingeniería; un ilustrador técnico produce las figuras a partir de fotos, CAD y
esquemas; un maquetador (DTP) aplica la plantilla corporativa y compone el documento;
un especialista en seguridad/normativa garantiza que el manual cumple la legislación
de máquinas; un terminólogo/traductor mantiene la coherencia de idioma; y un revisor
de calidad (QA) valida todo antes de publicar. La documentación se versiona y se
archiva junto con las decisiones de cada proyecto.

Ese reparto es exactamente lo que replicamos con subagentes.

## 2. Los subagentes propuestos

### 2.1 Coordinador editorial (orquestador) — el "jefe de proyecto"

Es la cara visible del sistema: el agente con el que habla el usuario.

- Hace la **entrevista de arranque** del proyecto: qué máquina es, qué tipo de
  manual se necesita (instalación, usuario/operación, mantenimiento, seguridad,
  despiece), idiomas, formato de entrega.
- Gestiona el **checklist de materiales** y va pidiendo lo que falta:
  1. Plantilla / manual de ejemplo (estructura y estilo a imitar).
  2. Fotografías e imágenes de la máquina y sus componentes.
  3. Inputs de funcionamiento: especificaciones, notas de ingeniería, secuencias
     de operación, datos eléctricos/mecánicos, mensajes de error.
  4. Información de seguridad: riesgos identificados, EPIs, condiciones de uso.
- Reparte el trabajo entre los subagentes y consolida sus entregas.
- Registra las decisiones del proyecto en la memoria (ver doc 03).

### 2.2 Analista de contenido / Documentalista

- Analiza la **plantilla de ejemplo** y extrae su estructura: capítulos, jerarquía
  de apartados, estilo de advertencias, numeración de figuras y tablas.
- Ingiere los inputs técnicos entregados y los organiza en una **escaleta**
  (content plan): qué información va a cada capítulo, y qué huecos hay.
- Devuelve al coordinador la lista de información que falta, para que la pida.

### 2.3 Redactor técnico

- Redacta los capítulos siguiendo la escaleta aprobada.
- Escribe en **lenguaje controlado**: frases cortas, imperativo en procedimientos,
  un paso por acción, terminología del glosario del proyecto.
- Redacta desde el punto de vista del usuario del manual (operario, técnico de
  servicio o instalador según el tipo de manual).

### 2.4 Especialista en seguridad y normativa

- Garantiza las secciones obligatorias según Reglamento (UE) 2023/1230,
  EN ISO 20607 e IEC/IEEE 82079-1 (detalle en doc 03).
- Redacta y coloca advertencias con la gradación correcta
  (PELIGRO / ADVERTENCIA / PRECAUCIÓN / AVISO) y los símbolos ISO 7010 adecuados.
- Verifica uso previsto, usos indebidos razonablemente previsibles, riesgos
  residuales, EPIs y datos de la placa de características.

### 2.5 Editor gráfico / Ilustrador técnico

- Recibe las fotografías e imágenes y las **cataloga** (componente, vista, capítulo
  al que pertenecen).
- Propone para cada figura: encuadre/recorte, llamadas numeradas (callouts),
  leyenda y posición en el documento.
- Mantiene la numeración de figuras y la lista de ilustraciones.
- Señala qué imágenes faltan o no tienen calidad suficiente, para que el
  coordinador las pida.

### 2.6 Maquetador (DTP)

- Aplica la plantilla corporativa: estilos de párrafo, portada, cabeceras/pies,
  tablas, índice general, índice de figuras, paginación.
- Compone el documento final (Word → PDF) insertando texto y figuras aprobados.
- Cuida los aspectos de imprenta digital: el Reglamento de Máquinas permite manual
  digital pero exige que sea **imprimible**.

### 2.7 Revisor / QA editorial

- Pasa el **checklist normativo** (secciones obligatorias presentes) y el
  **checklist de estilo** (terminología, numeración, referencias cruzadas,
  figuras citadas en el texto).
- Verifica coherencia entre capítulos y contra los inputs técnicos originales.
- Emite un informe de revisión; nada se entrega sin su visto bueno.

### 2.8 Terminólogo / Gestor de traducciones (fase 2)

- Mantiene el **glosario multiidioma** por familia de producto.
- Prepara los paquetes de traducción y verifica que las versiones traducidas
  conservan estructura, advertencias y numeración.

### 2.9 Archivero / Memoria (capa transversal, no conversacional)

No es un agente con el que se habla, sino la capa de persistencia: repositorio de
proyecto con materiales, versiones del manual, decisiones tomadas y glosario.
Todos los agentes leen de ahí y el coordinador escribe ahí. Detalle en doc 03.

## 3. Resumen del reparto

| Subagente | Entrada | Salida |
|---|---|---|
| Coordinador | Peticiones del usuario, entregas de subagentes | Preguntas, checklist, manual consolidado |
| Analista de contenido | Plantilla + inputs técnicos | Escaleta + lista de huecos |
| Redactor técnico | Escaleta + inputs | Capítulos redactados |
| Seguridad/normativa | Borrador + datos de riesgos | Secciones de seguridad + advertencias |
| Editor gráfico | Fotografías/imágenes | Figuras catalogadas con callouts y leyendas |
| Maquetador | Texto + figuras aprobados | Documento Word/PDF maquetado |
| QA | Documento maquetado | Informe de revisión / visto bueno |
| Terminólogo (F2) | Glosario + manual aprobado | Versiones multiidioma |

En la primera versión pueden fusionarse algunos roles para simplificar (por ejemplo,
Analista + Redactor, o QA dentro del Coordinador); la separación anterior es el
modelo completo al que tender.
