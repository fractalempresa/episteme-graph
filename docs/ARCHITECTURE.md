# Arquitectura del Sistema — EpistemGraph

## Visión general

EpistemGraph es un sistema de retroalimentación biyectiva entre el lenguaje natural (el contenido del paper) y la geometría (el estado de la investigación). El grafo no es solo un mapa de "lo que hay" — es un tablero de control de ingeniería del conocimiento.

```
┌─────────────────────────────────────────────────────────────┐
│                        FRONTEND                              │
│   Editor de texto ←→ Panel de control ←→ Grafo 3D (Three.js)│
└──────────────────────────┬──────────────────────────────────┘
                           │ WebSocket / REST
┌──────────────────────────▼──────────────────────────────────┐
│                        BACKEND (FastAPI)                      │
│  ┌─────────────┐  ┌──────────────┐  ┌───────────────────┐  │
│  │ Parser      │  │ NLP Engine   │  │ Crypto Module     │  │
│  │ (PDF/MD/DOC)│  │ (Claude API) │  │ (SHA256+Ed25519)  │  │
│  └──────┬──────┘  └──────┬───────┘  └─────────┬─────────┘  │
│         │                │                     │            │
│  ┌──────▼──────────────▼─────────────────────▼──────────┐  │
│  │              Graph Engine                              │  │
│  │  - Coordinate mapping                                  │  │
│  │  - State management (red/orange/green/violet/blue)     │  │
│  │  - Tension vector calculation                          │  │
│  │  - Ghost node projection                               │  │
│  └──────────────────────┬─────────────────────────────────┘  │
└─────────────────────────┼──────────────────────────────────┘
                          │
        ┌─────────────────┼─────────────────┐
        │                 │                 │
┌───────▼──────┐  ┌──────▼───────┐  ┌─────▼────────┐
│   Neo4j      │  │  PostgreSQL  │  │  External    │
│   (Graph DB) │  │  (Metadata)  │  │  APIs        │
│              │  │              │  │  CrossRef    │
│  Nodes       │  │  Documents   │  │  Semantic    │
│  Edges       │  │  Authors     │  │  Scholar     │
│  States      │  │  Hashes      │  │  arXiv       │
└──────────────┘  └──────────────┘  └──────────────┘
```

---

## Componentes principales

### 1. Parser de documentos
Convierte cualquier formato de entrada en una estructura semántica normalizada.

```python
# src/core/parser.py
class DocumentParser:
    def parse(self, document: bytes, format: str) -> DocumentStructure:
        """
        Retorna:
        - sections: lista de secciones identificadas
        - claims: lista de afirmaciones extraídas
        - citations: referencias bibliográficas
        - raw_text: texto completo segmentado
        """
```

### 2. Motor NLP (Claude API)
El corazón del sistema. Analiza coherencia, detecta inconsistencias y evalúa solidez argumentativa.

```python
# src/core/nlp_engine.py
class EpistemNLPEngine:
    def analyze_claim(self, claim: str, context: DocumentStructure) -> ClaimAnalysis:
        """
        Retorna:
        - has_support: bool (¿tiene respaldo bibliográfico?)
        - logical_consistency: float (0-1)
        - implicit_axioms: list[str]
        - contradictions: list[Contradiction]
        - node_state: NodeState (RED/ORANGE/GREEN/VIOLET/BLUE)
        """
    
    def analyze_coherence(self, section_a: Section, section_b: Section) -> CoherenceScore:
        """Detecta contradicciones entre secciones distantes del paper"""
    
    def suggest_expansion(self, graph_state: GraphState) -> list[Suggestion]:
        """'Tu geometría está descompensada — la discusión carece de masa relacional'"""
```

### 3. Motor de Grafo
Mapea el estado semántico a coordenadas y calcula tensiones geométricas.

```python
# src/graph/engine.py
class GraphEngine:
    def map_to_coordinates(self, node: DocumentNode) -> Coordinates3D:
        """Asigna posición en el espacio 3D basada en relaciones semánticas"""
    
    def calculate_tension(self, node: Node) -> TensionVector:
        """Vectores de tensión que deforman el grafo cuando hay inconsistencias"""
    
    def project_ghost(self, floating_node: Node) -> GhostNode:
        """Proyecta dónde debería conectarse un nodo para recuperar estabilidad"""
    
    def update_state(self, node_id: str, new_state: NodeState) -> GraphDelta:
        """Actualiza estado y propaga cambios a nodos conectados"""
```

### 4. Módulo Criptográfico
Genera la cadena de custodia intelectual.

```python
# src/crypto/tracer.py
class IntellectualTracer:
    def register_fragment(self, fragment: str, author: Author) -> IntellectualHash:
        """
        Genera:
        - content_hash: SHA-256 del fragmento
        - author_signature: firma Ed25519 del autor
        - timestamp: Unix timestamp verificable
        - graph_state_hash: estado del grafo en el momento de registro
        - epistem_trace_id: identificador único universal
        """
    
    def verify_authorship(self, trace_id: str) -> VerificationResult:
        """Verificación pública sin acceso al sistema original"""
    
    def export_custody_chain(self, document_id: str) -> CustodyChain:
        """Exporta cadena completa de autoría del documento"""
```

### 5. API REST

```
POST   /api/v1/documents              → Subir documento
GET    /api/v1/documents/{id}/graph   → Estado actual del grafo
POST   /api/v1/documents/{id}/analyze → Forzar re-análisis
PATCH  /api/v1/nodes/{id}/state       → Actualizar estado de nodo
GET    /api/v1/documents/{id}/audit   → Reporte de auditoría completo
POST   /api/v1/crypto/register        → Registrar fragmento criptográficamente
GET    /api/v1/crypto/verify/{trace}  → Verificación pública de autoría

WS     /ws/documents/{id}             → Stream de actualizaciones del grafo
```

---

## Estados del Grafo — Especificación

```typescript
// src/ui/types/graph.ts
enum NodeState {
  TENSION    = "RED",      // Error crítico, contradicción o falta total de evidencia
  FLOATING   = "ORANGE",   // En desarrollo, falta integración o pulido
  ANCHOR     = "GREEN",    // Argumento sólido y verificado
  SYNCRECIS  = "VIOLET",   // Intersección lograda entre áreas antes aisladas
  EXPANSION  = "BLUE"      // Sugerencia del sistema para profundizar
}

interface GraphNode {
  id: string
  state: NodeState
  position: { x: number, y: number, z: number }
  tension_vectors: TensionVector[]
  source_text: string         // Texto exacto del paper
  source_position: TextRange  // Posición en el documento original
  implicit_axioms: string[]
  suggestions: string[]
  crypto_trace?: IntellectualHash
}
```

---

## Flujo de datos en tiempo real

```
Usuario edita texto
      ↓
WebSocket → Backend
      ↓
Parser re-segmenta sección modificada
      ↓
NLP Engine analiza cambios (Claude API)
      ↓
Graph Engine recalcula estados y tensiones
      ↓
WebSocket → Frontend
      ↓
Three.js actualiza grafo 3D en tiempo real
(nodos cambian de color, tensiones se relajan o aumentan)
```

---

## Estructura de archivos

```
episteme-graph/
├── README.md
├── LICENSE
├── docs/
│   ├── ROADMAP.md
│   ├── ARCHITECTURE.md
│   ├── CONTRIBUTING.md
│   └── OSS_APPLICATION.md
├── src/
│   ├── core/
│   │   ├── parser.py          # Parser multi-formato
│   │   ├── nlp_engine.py      # Motor NLP (Claude API)
│   │   └── document.py        # Modelos de datos del documento
│   ├── graph/
│   │   ├── engine.py          # Motor de grafo
│   │   ├── coordinates.py     # Mapeo semántico → coordenadas 3D
│   │   ├── tension.py         # Cálculo de vectores de tensión
│   │   └── states.py          # Sistema de estados
│   ├── crypto/
│   │   ├── tracer.py          # Trazabilidad criptográfica
│   │   ├── signatures.py      # Firmas Ed25519
│   │   └── verify.py          # Verificador público
│   ├── api/
│   │   ├── main.py            # FastAPI app
│   │   ├── routes/
│   │   │   ├── documents.py
│   │   │   ├── graph.py
│   │   │   └── crypto.py
│   │   └── websocket.py       # WebSocket handler
│   └── ui/
│       ├── components/
│       │   ├── Graph3D.tsx     # Componente Three.js
│       │   ├── NodePanel.tsx   # Panel lateral de nodo seleccionado
│       │   └── StatusBar.tsx   # Estado general del documento
│       └── types/
│           └── graph.ts        # TypeScript types
├── public/
└── .github/
    └── ISSUE_TEMPLATE/
        ├── bug_report.md
        └── feature_request.md
```
