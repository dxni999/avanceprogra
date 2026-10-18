# Dizeo

## Progreso 1 de Programación III

Análisis, diseño y selección de una solución para organizar trabajadores y actividades en obras de construcción. El alcance comprende **5 obras, 20 trabajadores, 100 actividades y 5 usuarios**.

## Problema

Coordinar actividades entre obras requiere decidir su orden de atención e identificar trabajadores con la especialidad y el horario disponibles. La información dispersa puede generar cruces, esperas y actividades atrasadas. El proyecto relaciona prioridad, fecha límite, especialidad, jornada y avance.

## Integrantes y módulos

| Integrante | Responsabilidad preliminar |
|---|---|
| Daniel Valarezo | M1 Obras y M5 Seguimiento. Problema y documentación. |
| Esteban Figueroa | M2 Trabajadores y M4 Asignación. Disponibilidad y validación de horarios. |
| Julián Jiménez | M3 Actividades y prioridades. Comparador, cola de prioridad, UML y comparación técnica. |

La integración y la revisión se realizarán entre los tres integrantes.

## Alcance funcional

1. **Obras:** buscar por código, filtrar por estado, ordenar por entrega y consultar pendientes.
2. **Trabajadores:** buscar por código, filtrar por especialidad, consultar disponibilidad y calcular horas asignadas.
3. **Actividades y prioridades:** clasificar, ordenar, consultar la próxima pendiente y actualizar prioridad.
4. **Asignación:** consultar candidatos, detectar cruces, asignar y reprogramar.
5. **Seguimiento:** actualizar avance, identificar vencidas, contar por estado y calcular avance por obra.

Cada actividad pertenece a una obra y tiene como máximo una asignación activa. Un trabajador no puede tener cruces de horario. La prioridad es alta, media o baja; los empates se resuelven por fecha límite y código.

## Modelo y alternativas

El UML contiene cinco clases de dominio: **Obra, Actividad, Trabajador, Asignacion y Usuario**. Obra contiene sus actividades mediante composición. Las asignaciones relacionan actividad, trabajador y usuario responsable.

La alternativa A utiliza ArrayList y búsquedas lineales. La alternativa B utiliza HashMap por código, PriorityQueue para las actividades pendientes y ArrayList para las asignaciones. Se selecciona **B** por su correspondencia con las búsquedas y la extracción repetida de la próxima actividad.

Buscar un trabajador tiene costo O(w) en A y O(1) esperado en B. Elegir y retirar la próxima pendiente cuesta O(q) en A y O(log q) en B. El informe incluye las cotas espaciales, sus condiciones y las operaciones que mantienen el mismo costo en ambas alternativas.

## Estructura inicial del repositorio

| Ubicación | Contenido |
|---|---|
| `README.md` | Descripción, alcance, integrantes, módulos y alternativa seleccionada. |
| `docs/informe/` | Informe en Word y PDF. |
| `docs/presentacion/` | Presentación de nueve minutos, tres por integrante. |
| `docs/uml/dizeo.drawio` | Modelo de clases editable. |
| `docs/uml/REVISION.md` | Registro para la revisión del equipo. |
| `docs/plan/OBSERVACIONES.md` | Observaciones docentes que se conservarán para Progreso 2. |

Este avance contiene análisis y diseño. La implementación en Java corresponde a Progreso 2. El repositorio tiene historial Git local; su publicación en GitHub se realizará desde la cuenta del grupo.

## Riesgos técnicos y mitigación

| Riesgo | Mitigación |
|---|---|
| Cruces de horario | Comprobar jornada e intervalos antes de asignar o reprogramar. |
| Empates o prioridades incorrectas | Usar un único comparador por prioridad, fecha y código. |
| Cola desactualizada | Retirar y reinsertar al cambiar prioridad; sincronizar asignación y estado. |
| Datos duplicados o incompletos | Validar códigos únicos, campos obligatorios y avance entre 0 y 100 %. |

## Revisión y fuentes

El equipo debe revisar el informe y abrir el UML en diagrams.net para comprobar clases, métodos, asociaciones y multiplicidades. La declaración de IA y las referencias APA 7 constan en el informe. ChatGPT apoyó el análisis, la redacción y el diseño preliminar; la revisión grupal permanece pendiente.
