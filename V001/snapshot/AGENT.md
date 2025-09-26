# AGENT Guide — P vs NP Non‑Natural Proofs

Este documento instruye a agentes (humanos e IA) para trabajar en sesiones limpias, localizar la próxima iteración en el checklist maestro, ejecutar las 5 fases de cada documento y dejar todo marcado al cerrar.

---

## Inicio rápido para una sesión sin contexto

1) Abre y lee `MASTER_CHECKLIST.md`.
2) Identifica la sección "Próxima Iteración a Trabajar" y obtén:
   - Número de iteración (01–10)
   - Título
   - Ruta del archivo en `docs/iteration_XX.md`
3) Abre el archivo de la iteración y prepara las 5 fases usando `templates/iteration_template.md` como referencia estructural.
4) Ejecuta el trabajo fase por fase. Mantén trazabilidad con timestamps y estados.
5) Al finalizar, marca el progreso en `MASTER_CHECKLIST.md` (checkboxes y estado), añade una nota en "Notas de Progreso" y actualiza la "Próxima Iteración a Trabajar" si corresponde.

---

## Prompt de inicialización sugerido (para agentes IA)

Usa este prompt al iniciar una sesión limpia:

«Abre MASTER_CHECKLIST.md, identifica la “Próxima Iteración a Trabajar”, abre el `docs/iteration_XX.md` correspondiente y trabaja metódicamente las 5 fases siguiendo `templates/iteration_template.md`. Mantén estados (En Progreso/Completada) con timestamps por fase, y al cerrar: marca los checkboxes de la iteración en MASTER_CHECKLIST.md, actualiza su Estado, registra una entrada en “Notas de Progreso” y, si procede, establece la siguiente iteración en “Próxima Iteración a Trabajar”. No omitas documentación ni pasos.»

---

## Contrato de ejecución por iteración

- Entradas: `MASTER_CHECKLIST.md`, `docs/iteration_XX.md`, `templates/iteration_template.md`, referencias (p. ej., `Sota.md`, `base_de_conocimiento/`).
- Salidas: `docs/iteration_XX.md` actualizado con las 5 fases; `MASTER_CHECKLIST.md` con checkboxes y estado actualizados; nota en “Notas de Progreso”.
- Éxito: Todas las fases con contenido y estado ✅; checklist marcado; próxima iteración preparada (si aplica).
- Errores a evitar: Saltar fases; no registrar timestamps; no marcar el checklist; romper enlaces.

---

## Procedimiento detallado

1) Localizar el objetivo
- Abrir `MASTER_CHECKLIST.md` y leer “Próxima Iteración a Trabajar”.
- Verificar dependencias (no trabajar iteraciones bloqueadas).

2) Preparar el documento de trabajo
- Abrir `docs/iteration_XX.md`.
- Si el documento no sigue la estructura estándar, alinearlo con las secciones de la plantilla.

3) Ejecutar las 5 fases
- Fase 1: De dónde venimos (contexto, limitaciones, fundamentos)
- Fase 2: Dónde queremos ir (objetivo, criterios de éxito, impacto)
- Fase 3: Opciones para ir (A/B/C, decisión justificada)
- Fase 4: Vamos (desarrollo: matemático/algorítmico; verificación de no‑naturalidad/no‑relativización/no‑algebrización)
- Fase 5: A dónde hemos llegado (resultados, límites, conexiones, próximos pasos)

Para cada fase, anotar:
- Estado: ⏳ En Progreso → ✅ Completada
- Timestamps: inicio/fin

4) Cierre de iteración
- Marcar en `MASTER_CHECKLIST.md` las 5 fases y la casilla de “Iteración completada” cuando corresponda.
- Actualizar "Estado" de la iteración.
- Añadir una línea en "Notas de Progreso" (fecha, iteración, resumen de 1–2 frases).
- Actualizar “Próxima Iteración a Trabajar” si procede.

---

## Reglas de estilo y trazabilidad

- Idioma: Español.
- Matemáticas: usar bloques LaTeX cuando aplique.
- Enlaces relativos: conservar rutas como `docs/iteration_XX.md`.
- No borrar historial: ampliar/añadir, no eliminar evidencia salvo correcciones.
- Citar barreras: Razborov‑Rudich (Natural Proofs), Baker‑Gill‑Solovay (Relativización), Aaronson‑Wigderson (Algebrización) cuando sean relevantes.

---

## Operaciones frecuentes (guía)

- Determinar próxima iteración: leer “Próxima Iteración a Trabajar” en `MASTER_CHECKLIST.md`.
- Marcar checkboxes: cambiar "[ ]" a "[x]" en las fases completadas de la iteración.
- Registrar nota: añadir al final de “Notas de Progreso” con fecha ISO, ej. `2025-08-31 — Iteración 01: resumen`.

---

## Mapa de archivos

- `MASTER_CHECKLIST.md` — única fuente de verdad del estado.
- `AGENT.md` — esta guía operativa.
- `docs/iteration_01.md` … `docs/iteration_10.md` — documentos de trabajo por iteración.
- `templates/iteration_template.md` — referencia de estructura por fases.
- `Sota.md`, `base_de_conocimiento/` — contexto y estado del arte.

---

## Casos límite previstos

- Iteración bloqueada: si el checklist indica 🔒, no continuar; revisar dependencias.
- Inconsistencias de estado: si “Próxima Iteración” contradice checkboxes, priorizar checkboxes y registrar corrección en Notas.
- Falta de secciones: crear las secciones mínimas siguiendo la plantilla.

---

## Cierre

Si todos siguen este flujo, un agente sin contexto podrá iniciar, trabajar y dejar el rastro de progreso correctamente marcado en una sola sesión.»
