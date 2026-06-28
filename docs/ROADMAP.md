# Roadmap EpistemGraph

## Visión a 12 meses

Convertir EpistemGraph en el estándar abierto de auditoría epistemológica para investigación asistida por IA.

---

## Fase 1 — Fundamentos (Mes 1-2)
**Objetivo: MVP funcional con grafo 2D y análisis NLP básico**

### Core Engine
- [ ] Parser multi-formato: PDF, Markdown, DOCX, LaTeX
- [ ] Segmentación semántica del documento (secciones, párrafos, afirmaciones)
- [ ] Detección de afirmaciones sin cita bibliográfica
- [ ] Identificación de axiomas implícitos no declarados
- [ ] Motor de hash criptográfico por fragmento (SHA-256 + Ed25519)

### Grafo 2D
- [ ] Renderizado con D3.js
- [ ] Sistema de estados: Rojo / Naranja / Verde / Violeta / Azul
- [ ] Interacción: click en nodo → overlay con texto fuente
- [ ] Actualización en tiempo real al editar el documento

### Infraestructura
- [ ] Backend FastAPI (Python)
- [ ] Base de datos Neo4j para el grafo
- [ ] PostgreSQL para metadata y hashes
- [ ] API REST documentada con OpenAPI

---

## Fase 2 — Grafo 3D y Verificación (Mes 3-4)
**Objetivo: Experiencia de auditoría topológica completa**

### Grafo 3D
- [ ] Migración a Three.js con WebGL
- [ ] Vectores de tensión visibles entre nodos en conflicto
- [ ] "Fantasmas" de nodos: proyección de dónde debería conectarse un nodo flotante
- [ ] Navegación 3D: zoom, rotación, filtros por estado
- [ ] Panel de control de "Estado de Producción" con métricas del grafo

### Verificación Externa
- [ ] Integración CrossRef API: verificación de DOIs en tiempo real
- [ ] Integración Semantic Scholar: búsqueda de citas relacionadas
- [ ] Detección de alucinaciones: comparación de afirmaciones contra fuentes verificables
- [ ] Alerta visual cuando una cita no puede ser verificada externamente

### Trazabilidad Criptográfica
- [ ] Registro de autoría por fragmento con timestamp
- [ ] Firma digital del autor (Ed25519)
- [ ] Exportación de cadena de custodia intelectual (JSON verificable)
- [ ] Verificador público: cualquiera puede comprobar la autoría sin acceso al sistema

---

## Fase 3 — IA Profunda (Mes 5-6)
**Objetivo: Motor de análisis epistemológico asistido por Claude**

### Análisis Avanzado
- [ ] Detección de contradicciones lógicas entre secciones distantes del paper
- [ ] Mapa de axiomas fundamentales: qué supuestos sostienen toda la estructura
- [ ] Análisis de balance geométrico: "tu dimensión de discusión carece de masa relacional"
- [ ] Sugerencias de expansión contextualizadas por estado del grafo
- [ ] Índice maestro epistemológico: árbol lógico completo del paper

### Alertas y Recomendaciones
- [ ] Sistema de notificaciones: cambio visual sutil vs alerta de capa de realidad
- [ ] Priorización de zonas de mejora por impacto en la estabilidad del grafo
- [ ] Recomendaciones de investigación adicional para fortalecer nodos débiles
- [ ] Reporte de auditoría exportable (PDF con grafo + diagnóstico)

### API Pública
- [ ] SDK Python para integración con flujos de trabajo existentes
- [ ] Webhooks para editores académicos
- [ ] Documentación completa con ejemplos

---

## Fase 4 — Plataforma y Estándar (Mes 7-12)
**Objetivo: Ecosistema y adopción institucional**

### Colaboración
- [ ] Multi-usuario en tiempo real (WebSockets)
- [ ] Modo revisión por pares: el revisor navega el grafo del autor
- [ ] Historial de versiones del grafo (evolución temporal del paper)
- [ ] Comentarios anclados a nodos específicos del grafo

### Integraciones
- [ ] Plugin para Obsidian (gestión de conocimiento personal)
- [ ] Integración con Zotero (gestión bibliográfica)
- [ ] Conector arXiv: importar papers y auditar automáticamente
- [ ] Integración con SSRN y repositorios institucionales

### EpistemTrace — Estándar Abierto
- [ ] Especificación formal del protocolo de trazabilidad intelectual
- [ ] Registro público descentralizado de autoría (IPFS o similar)
- [ ] Certificación EpistemGraph para papers auditados
- [ ] Propuesta a organismos académicos internacionales (IEEE, ACM, etc.)

---

## Métricas de éxito

| Hito | Métrica | Mes objetivo |
|------|---------|--------------|
| MVP funcional | 10 papers auditados end-to-end | Mes 2 |
| Grafo 3D estable | 50 usuarios beta activos | Mes 4 |
| Motor IA completo | 500 papers procesados | Mes 6 |
| Plataforma pública | 1000 investigadores registrados | Mes 12 |
| Estándar EpistemTrace | Primera institución adoptante | Mes 12 |

---

## Dependencias críticas

- **Claude API**: motor de análisis semántico profundo (razonamiento sobre coherencia lógica)
- **Three.js**: renderizado 3D del grafo
- **Neo4j**: base de datos de grafos para relaciones complejas
- **CrossRef / Semantic Scholar**: verificación de citas en tiempo real
- **WebSockets**: actualización en tiempo real del grafo al editar
