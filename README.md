# Dizeo

## Progreso 1 de Programación III

Análisis, diseño y selección de una solución para organizar trabajadores y actividades en obras de construcción. El equipo delimita para este avance un alcance académico de **5 obras, 20 trabajadores, 100 actividades y 5 usuarios**. Según la información aportada por Julián Jiménez, Dizeo registra actualmente las asignaciones en Excel.

## Problema

Coordinar actividades entre obras requiere decidir su orden de atención e identificar trabajadores con la especialidad y el horario disponibles. La información dispersa puede generar cruces, esperas y actividades atrasadas. El proyecto relaciona prioridad, fecha límite, especialidad, jornada y avance. Los conflictos se analizan como riesgos del proceso; no se documentó un incidente concreto confirmado de la empresa.

## Integrantes y módulos

| Integrante | Responsabilidad preliminar |
|---|---|
| Daniel Valarezo | M1 Obras y M5 Seguimiento. Problema y documentación. |
| Esteban Figueroa | M2 Trabajadores y M4 Asignación. Disponibilidad y validación de horarios. |
| Julián Jiménez | M3 Actividades y prioridades. Comparador, cola de prioridad, UML y comparación técnica. |

La integración es compartida. Julián Jiménez confirmó la revisión grupal del informe y del UML y la autorización docente para entregar como equipo de tres. El registro se conserva en `docs/uml/REVISION.md`.

## Alcance funcional

1. **Obras:** buscar por código, filtrar por estado, ordenar por entrega y consultar pendientes.
2. **Trabajadores:** buscar por código, filtrar por especialidad, consultar disponibilidad y calcular horas asignadas.
3. **Actividades y prioridades:** clasificar, ordenar, consultar la próxima pendiente y actualizar prioridad.
4. **Asignación:** consultar candidatos, detectar cruces, asignar y reprogramar.
5. **Seguimiento:** actualizar avance, identificar vencidas, contar por estado y calcular avance por obra. El promedio da el mismo peso a cada actividad, aunque tengan tamaños distintos.

Cada actividad pertenece a una obra y tiene como máximo una asignación activa. Un trabajador no puede tener cruces de horario. La prioridad es alta, media o baja; los empates se resuelven por fecha límite y código.

## Modelo y alternativas

El UML contiene cinco clases de dominio: **Obra, Actividad, Trabajador, Asignacion y Usuario**. Obra contiene sus actividades mediante composición. Las asignaciones relacionan actividad, trabajador y usuario responsable. Cada multiplicidad se muestra junto al extremo correspondiente. El UML también identifica **GestorPrioridades** como servicio de M3, separado de las cinco clases de dominio.

La alternativa A utiliza ArrayList y búsquedas lineales. La alternativa B utiliza HashMap por código, PriorityQueue para las actividades pendientes y ArrayList para las asignaciones. Se selecciona **B** por su correspondencia con las búsquedas y la extracción repetida de la próxima actividad.

Buscar un trabajador tiene costo O(w) en A y O(1) esperado en B. Elegir y retirar la próxima pendiente cuesta O(q) en A y O(log q) en B. Retirar una pendiente distinta de la cabecera cuesta O(q) también en B. Consultar todas las alternativas ordenadas cuesta O(q log q) y O(q) temporal en ambas propuestas. El informe incluye las demás cotas y el costo de validar disponibilidad.

## Actividad prioritaria sin personal disponible

Si la cabecera no tiene trabajador compatible y libre, permanece pendiente y conserva su prioridad. El supervisor puede esperar o consultar alternativas. `GestorPrioridades.listarEnOrden()` genera una copia, sin modificar la cola original. Si se elige otra actividad, se revalidan especialidad, jornada y cruces. Solo una asignación confirmada permite retirar la seleccionada; si no es la cabecera, se usa `remove(objeto)`, O(q). Si falla la validación, ninguna pendiente se retira.

`GestorPrioridades.cambiarPrioridad(codigo, valor)` controla retirar, modificar y reinsertar. El cambio de prioridad de Actividad tiene visibilidad de paquete y se invoca desde el servicio.

## Estructura inicial del repositorio

| Ubicación | Contenido |
|---|---|
| `README.md` | Descripción, alcance, integrantes, módulos y alternativa seleccionada. |
| `docs/informe/` | Informe en Word y PDF. |
| `docs/presentacion/` | Presentación de nueve minutos y treinta segundos, tres minutos y diez segundos por integrante. |
| `docs/uml/dizeo.drawio` | Modelo editable en dos vistas: dominio y servicio de prioridades. |
| `docs/uml/REVISION.md` | Confirmación de revisión grupal y cambios incorporados. |
| `docs/plan/OBSERVACIONES.md` | Observaciones docentes que se conservarán para Progreso 2. |

Este avance contiene análisis y diseño. La implementación en Java corresponde a Progreso 2. El repositorio tiene historial Git local; su publicación en GitHub se realizará desde la cuenta del grupo.

## Riesgos técnicos y mitigación

| Riesgo | Mitigación |
|---|---|
| Cruces de horario | Comprobar jornada e intervalos antes de asignar o reprogramar. |
| Empates o prioridades incorrectas | Usar un único comparador por prioridad, fecha y código. |
| Cola desactualizada | Canalizar cambios por GestorPrioridades; consultar alternativas con una copia y sincronizar asignación y cola. |
| Datos duplicados o incompletos | Validar códigos únicos, campos obligatorios y avance entre 0 y 100 %. |

## Revisión y fuentes

La revisión grupal del informe y del UML fue confirmada por Julián Jiménez. El diagrama puede abrirse en diagrams.net para inspeccionar las dos vistas. La declaración de IA y las referencias APA 7 constan en el informe. ChatGPT apoyó el análisis, la redacción y el diseño preliminar; el equipo mantiene la responsabilidad académica y técnica.
