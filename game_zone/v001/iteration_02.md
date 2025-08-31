# Iteración 02: Launcher Mínimo

## Estado del Progreso
- [ ] Fase 1: De dónde venimos
- [ ] Fase 2: Dónde queremos ir
- [ ] Fase 3: Opciones para ir
- [ ] Fase 4: Vamos (Ejecución)
- [ ] Fase 5: A dónde hemos llegado

---

## Fase 1: De dónde venimos

### Contexto Previo
- Iteración 01 completada: componentes mínimos identificados
- Estructura teatro-computacional/ creada
- Código base extraído del state-machine-mcp-driver

### Limitaciones Identificadas
- El launcher original tiene demasiadas abstracciones
- Sistema de plugins innecesario para nuestros 3 servidores
- Complejidad de configuración excesiva

### Fundamentos Teóricos
- Patrón Launcher para orquestación de servicios
- Gestión de procesos para servidores MCP
- Configuración declarativa vs programática

---

## Fase 2: Dónde queremos ir

### Objetivo Principal
Implementar un MinimalLauncher que pueda arrancar los 3 servidores MCP (Box Paradox, Recursive Mirage, Algebraic Mirror) de forma simple y confiable.

### Criterios de Éxito
- Launcher funcional con configuración simple
- Capacidad de arrancar múltiples servidores MCP
- Sistema de health check básico
- Interfaz limpia sin plugins innecesarios

### Impacto Esperado
Base para las Iteraciones 03-05 donde implementaremos cada servidor MCP individual.

---

## Fase 3: Opciones para ir

### Opción A: Copia Directa del Launcher Original
**Descripción:** Tomar el launcher completo y quitar funcionalidades
**Ventajas:** Funcionalidad completa garantizada
**Desventajas:** Mantiene complejidad innecesaria
**Viabilidad:** Media - mucho trabajo de limpieza

### Opción B: Launcher Básico desde Cero
**Descripción:** Implementar solo lo esencial para arrancar procesos MCP
**Ventajas:** Código limpio y enfocado
**Desventajas:** Riesgo de perder funcionalidad crítica
**Viabilidad:** Alta - control total del código

### Opción C: Híbrido Basado en xplus1-app
**Descripción:** Extraer exactamente lo que usa xplus1-app más configuración para múltiples servidores
**Ventajas:** Balance entre funcionalidad y simplicidad
**Desventajas:** Limitado por las necesidades de xplus1-app
**Viabilidad:** Alta - enfoque pragmático

### Decisión Final
Opción B: Launcher básico desde cero, implementando solo la funcionalidad esencial identificada en Iteración 01.

---

## Fase 4: Vamos (Ejecución)

### Desarrollo del MinimalLauncher

```typescript
// teatro-computacional/launcher/minimal-launcher.ts
export interface ServerConfig {
  name: string;
  port: number;
  protocol: 'mcp';
  command?: string;
  args?: string[];
}

export class MinimalLauncher {
  private servers: Map<string, Process> = new Map();
  
  async launchMCPServers(configs: ServerConfig[]): Promise<void> {
    // Implementación básica sin plugins
  }
  
  async healthCheck(): Promise<ServerStatus[]> {
    // Verificación simple de estado
  }
  
  async shutdown(): Promise<void> {
    // Cierre limpio de todos los procesos
  }
}
```

### Configuración Simplificada

```json
// teatro-computacional/config/servers.json
{
  "servers": [
    {
      "name": "box-paradox",
      "port": 3001,
      "protocol": "mcp"
    },
    {
      "name": "recursive-mirage", 
      "port": 3002,
      "protocol": "mcp"
    },
    {
      "name": "algebraic-mirror",
      "port": 3003,
      "protocol": "mcp"
    }
  ]
}
```

### Verificación de Simplicidad
- Sin sistema de plugins
- Sin middleware complejo
- Configuración declarativa simple
- Enfoque solo en arranque y health check

### Pasos Críticos
1. Implementar MinimalLauncher básico
2. Crear sistema de configuración JSON
3. Implementar health check simple
4. Crear script de prueba
5. Documentar API del launcher

---

## Fase 5: A dónde hemos llegado

### Resultados Obtenidos
- [ ] MinimalLauncher implementado y funcional
- [ ] Sistema de configuración JSON simple
- [ ] Health check básico implementado
- [ ] Script de prueba creado
- [ ] Documentación de API completada

### Limitaciones Encontradas
- [Por completar después de la ejecución]

### Conexiones con Otras Iteraciones
- Iteración 03: Primer servidor MCP (Box Paradox) usará este launcher
- Iteración 04: Segundo servidor MCP (Recursive Mirage) 
- Iteración 05: Tercer servidor MCP (Algebraic Mirror)
- Iteración 07: Runtime integrará con este launcher

### Próximos Pasos
- Implementar BoxParadoxServer en Iteración 03
- Probar launcher con primer servidor real

---

## Metadatos de la Iteración

**Fecha de Inicio:** [Por definir]
**Fecha de Finalización:** [Por completar]
**Agente Responsable:** Teatro Computacional Agent
**Estado:** Pendiente
**Nivel de Confianza:** 8

---

## Referencias y Enlaces

### Recursos Base
- Iteración 01: Arquitectura y componentes identificados
- MCP Protocol Specification

### Iteraciones Relacionadas
- Depende de: Iteración 01
- Habilita: Iteraciones 03, 04, 05

### Recursos Externos
- Node.js Process API
- JSON Schema para configuración
