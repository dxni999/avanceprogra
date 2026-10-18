# Dizeo

## Progreso 1 de Programación III

Proyecto de análisis, diseño y selección de una solución para planificar trabajadores y actividades de obra. El caso procede del levantamiento de requerimientos de Dizeo realizado en Ingeniería de Requerimientos.

Este repositorio contiene exclusivamente la documentación del Progreso 1. La implementación en Java corresponde al plan para Progreso 2.

## Problema y objetivo

Coordinar obras que comparten trabajadores, especialidades y horarios requiere comprobar disponibilidad, precedencias y traslados. La propuesta organiza información para reducir asignaciones incompatibles y facilitar el seguimiento. Las situaciones del caso son hipótesis que el equipo deberá validar con registros y entrevistas; no se presentan resultados de un piloto realizado.

El objetivo del avance es formular el problema, definir módulos, elaborar el modelo orientado a objetos, comparar dos alternativas con estructuras y algoritmos y fundamentar una selección antes de programar.

## Integrantes y responsabilidad preliminar

| Integrante | Componentes previstos |
|---|---|
| Daniel Valarezo | Obras y seguimiento. Coordinación de documentación. |
| Esteban Figueroa | Trabajadores, disponibilidad, planificación y asignación. Integración con persistencia. |
| Julián Jiménez | Actividades, prioridades, dependencias, UML y comparación técnica. |

El equipo está conformado por Daniel Valarezo, Esteban Figueroa y Julián Jiménez. Los cinco módulos se distribuyen entre los tres, con integración y revisión compartidas. El reparto corresponde al plan de trabajo y no acredita implementación ya realizada.

## Alcance funcional

1. Obras: registrar compromisos, filtrar y ordenar entregas e identificar tareas vencidas o sin responsable.
2. Trabajadores y disponibilidad: consultar especialidades y horarios, calcular carga y disponibilidad.
3. Actividades y prioridades: definir tareas, ordenar por prioridad/fecha/código y detectar ciclos.
4. Planificación y asignación: sugerir equipos, validar restricciones, consultar agendas y reprogramar con motivo.
5. Seguimiento e incidencias: distinguir avance informado y validado, resolver incidencias y calcular indicadores.

El informe desarrolla cinco operaciones por módulo, actores, datos, reglas, relaciones y responsables. No se incorporan nómina, compras, facturación, aplicación móvil, rutas óptimas ni optimización global automática.

## Diseño y alternativa seleccionada

El UML propone Obra, Actividad, Trabajador, Disponibilidad, Asignacion, Usuario, ReporteAvance, Incidencia, PlanSemanal y EventoAuditoria. Usa composición cuando corresponde y un atributo de rol para evitar herencia artificial.

La alternativa A utiliza listas, búsqueda lineal, matriz de adyacencia y DFS. La alternativa B propone HashMap, índice por especialidad, TreeMap por trabajador, PriorityQueue y grafo con listas de adyacencia y Kahn. Se selecciona B por consultas repetidas y dependencias dispersas, con sus costos de mantenimiento e integridad explicados en el informe.

El diseño considera prioridad alta, media y baja, con desempate por fecha comprometida y código. La prioridad no elimina las restricciones de especialidad, jornada, dependencias, equipo completo ni traslado. Java Swing y PostgreSQL son restricciones de la implementación futura.

## Estructura inicial del repositorio

| Ubicación | Contenido |
|---|---|
| `README.md` | Descripción del problema, alcance, alternativa, integrantes y estructura. |
| `docs/informe/Informe_Dizeo_Progreso1.docx` y su PDF | Informe técnico editable y versión de entrega, con portada y formato del documento de referencia. |
| `docs/presentacion/Presentacion_Dizeo_Progreso1_Final.pptx` | Presentación editable con notas, referencias y distribución de 9 minutos y 30 segundos entre tres expositores. |
| `docs/uml/dizeo.drawio` | UML preliminar editable en dos vistas. |
| `docs/uml/REVISION.md` | Registro para la revisión real del equipo. |
| `docs/plan/OBSERVACIONES.md` | Registro de observaciones docentes y mejoras obligatorias para Progreso 2. |

El repositorio tiene historial Git local con un commit inicial de documentación. No tiene remoto configurado y no se ha publicado en una cuenta de GitHub.

## Revisión y publicación

1. Abrir el informe y la presentación. Revisar la coherencia entre problema, módulos, clases y alternativas.
2. Abrir `docs/uml/dizeo.drawio` en diagrams.net. Revisar las dos vistas y registrar cambios y participantes en REVISION.md. El diagrama no se considera revisado por el equipo hasta realizar esa actividad.
3. Confirmar el reparto entre los tres integrantes y ensayar aproximadamente 3 minutos y 10 segundos por persona.
4. Abrir esta carpeta como repositorio existente en la herramienta Git que use el grupo y publicarla en su cuenta de GitHub. Conservar el historial local y registrar la URL real. No se inventa una dirección de repositorio.
5. Ensayar la presentación para que todos participen y conservar las observaciones del docente como requisitos de mejora.

## Plan para Progreso 2

Validar alcance y contratos de clases; implementar estructuras y reglas; contrastar alternativas en casos pequeños; integrar Swing, servicio y PostgreSQL; y verificar concurrencia, permisos, auditoría, recuperación y rendimiento conforme a los requisitos. El informe describe responsables, hitos relativos, riesgos y mitigaciones. No se afirman pruebas ni implementación terminadas.

## Uso de inteligencia artificial

ChatGPT se utilizó como apoyo en análisis, redacción y diseño preliminar. Se incorporan borradores del informe, UML y presentación. El equipo revisará y comprenderá el contenido. La revisión grupal permanece pendiente.

## Fuentes

Las referencias completas APA 7 están en el informe y las fuentes de cada diapositiva están en sus notas. Incluyen el documento de requerimientos, Durdyev y Hosseini, Gómez Sánchez y colaboradores, Hendrickson, documentación de Oracle y documentación de PostgreSQL.
