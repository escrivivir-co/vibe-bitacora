# Instrucciones para el Agente IA: Desarrollo de Aplicación Angular + Three.js

## Objetivo General
Desarrollar una aplicación web en Angular (latest) con integración Three.js para visualizar una arquitectura de bots y trayectorias de mensajes, usando comunicación reactiva RxJS y Socket.io. El objetivo es construir la demo funcional descrita en el plan, asegurando modularidad, sincronización y pruebas completas.

## Alcance y Entregables Clave
1. **Bridge RxJS-Socket.io:** Implementa un bridge en TypeScript (`rxjs-bridge.ts`) que conecta eventos desde Socket.io y distribuye mensajes mediante Subjects y Observables RxJS, gestionando rooms y canales diferenciados (Sys, App, UI).
2. **UI Angular:** Construye los componentes `BotListComponent` y `MessagePanelComponent` con filtros, gestión de estados y control de bots, integrando los servicios del bridge.
3. **Escena Three.js:** Renderiza una esfera central (Socket.io), cuatro espirales cardinales con bots (dos por punto cardinal), y trayectorias animadas de mensajes usando `THREE.Curve`. Diferencia los canales por color.
4. **Pipeline de Datos:** Desarrolla el pipeline RxJS (`message-pipeline.ts`) para transformar, filtrar y distribuir los mensajes en tiempo real a Angular y Three.js, soportando reconexiones y optimizaciones con operators como `scan`, `filter`, `mergeMap`, `throttle`, `debounce`.
5. **Demo-Secuencia:** Implementa un cliente externo (`demo-client.ts`) que simula mensajes de salud del sistema (broadcast) y el clic usuario en un bot, validando animaciones sincronizadas.
6. **Testing & QA:** Desarrolla pruebas unitarias (Jasmine/Karma), end-to-end (Cypress), tests de rendimiento (frame-rate, garbage collection), y auditoría de seguridad Socket.io.
7. **Documentación:** Entrega README, diagramas de arquitectura (PlantUML/Mermaid), guía de desarrollo local, y referencia API del bridge RxJS.

## Detalles Técnicos y Funcionales
- Los bots se disponen en un cubo (escena Three.js) en cuatro puntos cardinales y en modalidad espiral.
- Los mensajes visualizados muestran trayectorias entre el centro y los puntos cardinales, simulando entradas/salidas por ROOM.
- Cada ROOM de Socket.io asocia bots y permite broadcast intercanal.
- El pipeline de datos separa y direcciona mensajes simultáneamente a la UI Angular y la escena 3D.
- La secuencia de demo verifica la correcta sincronización de datos entre todos los módulos.

## Requisitos de Implementación
- Código modular y documentado inline.
- Tests completos para cada bloque.
- Estructura de carpetas siguiendo el plan (`rxjs-bridge.ts`, componentes Angular, `scene.ts`, `message-pipeline.ts`, demo, tests, docs).
- Logging en demo para evaluar sincronización y debugging.
- Uso de Docker Compose para desarrollo local.

## Responda siempre con:
- Acciones específicas, fragmentos de código relevantes, y recomendaciones en cada respuesta.
- Documentación de avances y preguntas abiertas en JSON bajo encabezado `Estado Actual (JSON)`.
- Sugerencias sobre los siguientes pasos según el progreso o dudas detectadas.

## Inicie el desarrollo por:
Arquitectura de Comunicación y Bridge RxJS-Socket.io, garantizando aislamiento de rooms, canalización de eventos y documentación del flujo de datos.

---

Este prompt proporciona contexto, estructura, objetivos técnicos, criterios de entrega y el orden de implementación óptimo para lanzar y guiar el agente[web:1].