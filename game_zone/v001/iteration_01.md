# Iteración 01: Análisis y Extracción del Core

## Estado del Progreso
- [ ] Fase 1: De dónde venimos
- [ ] Fase 2: Dónde queremos ir
- [ ] Fase 3: Opciones para ir
- [ ] Fase 4: Vamos (Ejecución)
- [ ] Fase 5: A dónde hemos llegado

---

## Fase 1: De dónde venimos

### Contexto Previo
- Tenemos el proyecto `state-machine-mcp-driver` con arquitectura compleja
- Existe el ejemplo `xplus1-app` como referencia mínima
- Necesitamos extraer componentes esenciales para Teatro Computacional

### Limitaciones Identificadas
- Vibecoding excesivo con capas y capas de código
- Sistema de plugins complejo innecesario para nuestro caso
- Múltiples abstracciones que oscurecen la funcionalidad core

### Fundamentos Teóricos
- Arquitectura MCP (Model Context Protocol)
- State machines y transiciones de estado
- Launcher pattern para orquestación de servicios

---

## Fase 2: Dónde queremos ir

### Objetivo Principal
Extraer los componentes mínimos necesarios del `state-machine-mcp-driver` para crear una base limpia que soporte los tres shows de pruebas no-naturales.

### Criterios de Éxito
- Identificación clara de dependencias mínimas
- Arquitectura simplificada documentada
- Estructura de carpetas creada
- Componentes core extraídos sin vibecoding

### Impacto Esperado
Base sólida y limpia para implementar los tres servidores MCP que representarán las pruebas no-naturales de P vs NP.

---

## Fase 3: Opciones para ir

### Opción A: Extracción Completa
**Descripción:** Extraer todo el código relevante y simplificar después
**Ventajas:** No perdemos funcionalidad importante
**Desventajas:** Mantenemos complejidad innecesaria
**Viabilidad:** Media - requiere mucho trabajo de limpieza

### Opción B: Reimplementación desde Cero
**Descripción:** Crear todo nuevo basándonos solo en los conceptos
**Ventajas:** Código limpio y enfocado
**Desventajas:** Riesgo de perder funcionalidad crítica
**Viabilidad:** Baja - demasiado trabajo

### Opción C: Extracción Selectiva Guiada por xplus1-app
**Descripción:** Usar xplus1-app como guía para identificar qué extraer exactamente
**Ventajas:** Equilibrio entre funcionalidad y simplicidad
**Desventajas:** Dependemos de que el ejemplo sea completo
**Viabilidad:** Alta - enfoque práctico y eficiente

### Decisión Final
Opción C: Extracción selectiva guiada por el análisis detallado de qué componentes usa realmente xplus1-app.

---

## Fase 4: Vamos (Ejecución)

### Desarrollo de la Arquitectura

```typescript
// Componentes identificados para extracción:
interface MinimalArchitecture {
  launcher: {
    MCPServerLauncher: 'Para arrancar servidores MCP';
    ProcessManager: 'Gestión básica de procesos';
  };
  runtime: {
    BasicRuntime: 'Ejecución de StateGraph sin plugins';
    StateExecutor: 'Motor de transiciones de estado';
  };
  adapter: {
    SimpleMCPAdapter: 'Interfaz directa con SDK oficial MCP';
  };
  orchestrator: {
    ChannelManager: 'Gestión básica de canales';
  };
}
```

### Análisis de Dependencias de xplus1-app

1. **getBasicRuntimeConfig.ts** → Configuración mínima del Runtime
2. **xplus1-config.json** → Patrón de configuración UI/comportamiento  
3. **xplus1-game.ts** → Estructura StateGraph básica
4. **xplus1-app.ts** → Punto de entrada y orquestación

### Verificación de Simplicidad
- Solo componentes que realmente usa xplus1-app
- Sin sistema de plugins complejo
- Sin middleware innecesario
- Interfaz directa con MCP SDK oficial

### Pasos Críticos
1. Analizar imports y dependencias reales de xplus1-app
2. Mapear cada componente a funcionalidad mínima
3. Crear estructura de carpetas teatro-computacional/
4. Extraer solo el código esencial identificado
5. Documentar decisiones de arquitectura

---

## Fase 5: A dónde hemos llegado

### Resultados Obtenidos
- [ ] Lista de componentes mínimos identificados
- [ ] Estructura de carpetas teatro-computacional/ creada
- [ ] Código base extraído sin vibecoding
- [ ] Documentación de arquitectura simplificada

### Limitaciones Encontradas
- [Por completar después de la ejecución]

### Conexiones con Otras Iteraciones
- Iteración 02: Usará el MinimalLauncher extraído aquí
- Iteración 03-05: Usarán la estructura MCP Server base
- Iteración 06: Usará el patrón StateGraph simplificado

### Próximos Pasos
- Implementar MinimalLauncher en Iteración 02
- Configurar primer servidor MCP en Iteración 03

---

## Metadatos de la Iteración

**Fecha de Inicio:** 2025-08-31
**Fecha de Finalización:** [Por completar]
**Agente Responsable:** Teatro Computacional Agent
**Estado:** En Progreso
**Nivel de Confianza:** 8

---

## Referencias y Enlaces

### Recursos Base
- state-machine-mcp-driver/examples/xplus1-app/
- SDK oficial Model Context Protocol

### Iteraciones Relacionadas
- Preparación para Iteraciones 02-10

### Recursos Externos
- Documentación MCP oficial
- Patrón State Machine
