# EpistemGraph 🧠

> **Digital Twin epistemológico para la investigación académica verificable**
> Auditoría topológica en tiempo real · Trazabilidad criptográfica de autoría · Detección de alucinaciones y axiomas

[![License: AGPL v3](https://img.shields.io/badge/License-AGPL%20v3-blue.svg)](LICENSE)
[![Status: Active Development](https://img.shields.io/badge/Status-Active%20Development-green)]()
[![Open Source](https://img.shields.io/badge/Open%20Source-Yes-blue)]()

---

## ¿Qué es EpistemGraph?

EpistemGraph convierte cualquier paper o investigación en un **grafo 3D/4D vivo** que representa el estado de salud epistemológica del documento en tiempo real.

No es un visualizador. Es un **tablero de control de ingeniería del conocimiento**.

Cada sección, cita, argumento y conclusión se mapea como un nodo en el espacio. La geometría del grafo **es** el estado de la investigación: cuando hay una contradicción, el grafo se deforma. Cuando la evidencia es sólida, el grafo se estabiliza. La topología no miente.

---

## El problema que resuelve

La investigación académica actual tiene tres crisis simultáneas:

1. **Crisis de verificabilidad**: No existe un mecanismo estándar para auditar la solidez lógica de un paper en tiempo real durante su producción.
2. **Crisis de autoría**: La IA generativa hace imposible distinguir contribuciones humanas originales de contenido sintético sin trazabilidad criptográfica.
3. **Crisis de confianza en IA**: Los modelos de lenguaje alucinan referencias, datos y conclusiones. No existe una capa que intercepte esto durante el flujo de trabajo investigativo.

EpistemGraph ataca los tres simultáneamente.

---

## Cómo funciona

### Ciclo de Auditoría Topológica

```
Paper (texto)  →  NLP Semántico  →  Grafo 3D  →  Detección de tensión  →  Alerta → Resolución → Re-estabilización
```

**Fase A — Inyección y Detección**
- El motor NLP analiza coherencia, suficiencia de evidencia y solidez de conclusiones
- Detecta "Zonas de Estrés": afirmaciones sin respaldo, contradicciones lógicas, citas no verificables
- Traduce cada segmento a coordenadas en el espacio 3D

**Fase B — Diagnóstico Geométrico**
- El grafo refleja el estado: nodos colapsados = argumentos débiles
- Al interactuar con un nodo, aparece el texto exacto responsable de la inconsistencia
- El sistema proyecta un "fantasma" mostrando dónde debería conectarse el nodo para recuperar estabilidad

**Fase C — Validación y Re-estabilización**
- El investigador corrige el paper
- El sistema re-analiza y actualiza el grafo en tiempo real
- El espacio 3D "se relaja" cuando la zona de mejora es satisfecha

### Sistema de Estados del Grafo

| Color | Estado Geométrico | Significado |
|-------|-------------------|-------------|
| 🔴 Rojo | Nodo de Tensión | Error crítico, contradicción o falta total de evidencia |
| 🟠 Naranja | Nodo Flotante | En desarrollo. Falta integración o evidencia |
| 🟢 Verde | Nodo Ancla | Argumento sólido y verificado |
| 🟣 Violeta | Nodo de Síncrecis | Intersección lograda entre áreas antes aisladas |
| 🔵 Azul | Nodo de Expansión | Sugerencia del sistema para profundizar |

---

## Componente de Trazabilidad Criptográfica

Cada idea original registrada en el sistema genera un **hash criptográfico** que enlaza:
- La idea/fragmento original
- El autor (identidad verificada)
- El timestamp de creación
- El estado del grafo en ese momento

Esto crea una **cadena de custodia intelectual** inmutable: prueba verificable de autoría original independiente de cualquier plataforma. Base para un nuevo paradigma de propiedad intelectual en la era de la IA.

---

## Stack Técnico

```
Frontend:     React + Three.js (grafo 3D) + D3.js (layouts)
Backend:      FastAPI (Python)
NLP Engine:   Claude API (análisis semántico) + modelos locales (Ollama fallback)
Crypto:       SHA-256 + firma digital (Ed25519)
DB:           Neo4j (grafo) + PostgreSQL (metadata)
Realtime:     WebSockets
```

---

## Roadmap

### v0.1 — MVP (mes 1-2)
- [ ] Parser de documentos (PDF, Markdown, DOCX)
- [ ] Motor NLP básico: detección de afirmaciones sin cita
- [ ] Grafo 2D interactivo con estados de color
- [ ] Hash criptográfico de autoría por fragmento

### v0.2 — Grafo 3D (mes 3-4)
- [ ] Renderizado 3D con Three.js
- [ ] Detección de contradicciones lógicas entre secciones
- [ ] Verificación de citas en tiempo real (CrossRef, Semantic Scholar APIs)
- [ ] Panel de control de estado de producción

### v0.3 — IA Integrada (mes 5-6)
- [ ] Detección de alucinaciones con verificación externa
- [ ] Sugerencias de expansión del grafo ("tu geometría está descompensada")
- [ ] Exportación de árbol lógico y mapa axiomático
- [ ] API pública para integración con editores académicos

### v1.0 — Plataforma (mes 7-12)
- [ ] Multi-usuario y colaboración en tiempo real
- [ ] Integración con repositorios académicos (arXiv, SSRN)
- [ ] Módulo de revisión por pares asistida por grafo
- [ ] Estándar abierto de trazabilidad intelectual (EpistemTrace)

---

## Por qué es Open Source

Este proyecto es infraestructura epistemológica, no un producto. La verificabilidad del conocimiento académico no puede depender de una empresa privada. El protocolo de trazabilidad intelectual debe ser un bien común.

Cualquier investigador, institución o sistema de IA debe poder auditar, implementar y extender este sistema libremente.

---

## Contribuir

Ver [CONTRIBUTING.md](docs/CONTRIBUTING.md)

Issues etiquetados con `good first issue` son el punto de entrada.

---

## Licencia

MIT — libre para usar, modificar y distribuir con atribución.

---

## Contacto

Proyecto iniciado por un desarrollador colombiano como respuesta a la crisis de confianza epistemológica en la era de la IA generativa.

*"La geometría no miente. Si tu investigación está rota, el grafo lo muestra."*
