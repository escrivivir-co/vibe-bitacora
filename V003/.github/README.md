# Astilleros Retro - Sistema de GitHub Copilot Agents

Este documento explica cómo usar el sistema de Astilleros Retro implementado como GitHub Copilot agents.

## 🏗️ Estructura del Sistema

```
.github/
├── copilot-instructions.md     # Instrucciones generales del workspace
├── chatmodes/                  # Agentes especializados
│   ├── githubeador.chatmode.md # Experto en estándares VS Code Copilot
│   └── astilleador.chatmode.md # Constructor de estructuras
├── instructions/               # Instrucciones específicas
│   ├── framework-analysis.md   # Análisis de frameworks
└── prompts/                   # Prompts reutilizables
    ├── 
    └──  
```

## 🚢 Filosofía del Sistema

**Astilleros Retro** es un entorno especializado para el desarrollo, mantenimiento y optimización de frameworks de IA y sistemas inteligentes, inspirado en la metáfora naval donde los "astilleros" representan el lugar donde se construyen, reparan y mejoran las "naves" (frameworks y sistemas).

### Principios Fundamentales
- **Excelencia Técnica**: Cada componente debe cumplir estándares superiores de calidad
- **Documentación Rigurosa**: Todo debe estar documentado con precisión técnica
- **Evolución Continua**: Los sistemas deben mejorar constantemente a través de iteraciones
- **Meta-Arquitectura**: Capacidad de los sistemas para entenderse y mejorarse a sí mismos

## 🤖 Agentes Especializados

### Githubeador 📋
**Función**: Experto en estándares de VS Code Copilot
- Explica la estructura `.github` requerida
- Detalla formatos oficiales para instructions, chatmodes y prompts
- Enseña las mejores prácticas de implementación
- Valida conformidad con estándares oficiales

**Cuándo usar**: Cuando necesites entender o validar la estructura de GitHub Copilot agents.

### Astilleador 🔧
**Función**: Constructor de estructuras basado en especificaciones
- Aprende de Githubeador sobre los estándares
- Analiza documentos existentes (como `Astilleros.md`)
- Crea estructuras completas de `.github` 
- Implementa chatmodes, instructions y prompts

**Cuándo usar**: Cuando necesites crear o adaptar sistemas al formato GitHub Copilot agents.

## 🛠️ Cómo Usar el Sistema

### 1. Activar un Agente
```
@githubeador [a partir de un archivo de contexto, generar un chatmode]
@astilleador [anfritrión para acceder al resto de chatmodes]
```

### 2. Workflow Típico

#### Para Crear un Nuevo Sistema:
1. **Consulta a Githubeador**: "¿Cuál es la estructura estándar para chatmodes?"
2. **Solicita a Astilleador**: "Crea un chatmode basado en este documento"
3. **Valida con Githubeador**: "¿Esta estructura cumple los estándares?"

*Este sistema representa la evolución de Astilleros Retro hacia un formato estándar de GitHub Copilot, manteniendo la excelencia técnica y la capacidad de auto-mejora que caracteriza al proyecto original.*