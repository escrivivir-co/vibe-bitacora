# HyperGraph + Multi-Context System - LLM Reference

**Status:** CONCEPTUAL → IMPLEMENTATION PENDING | **Date:** 2025-09-30 | **Integration:** Retro Framework v5.0

## CORE CONCEPT

**HyperGraph:** Semantic knowledge storage using hypergraphs + dynamic ontologies + category theory + self-organization

**Multi-Context System:** Dual-format documentation (Human ↔ LLM) + multi-angular views + transparent context injection

**Integration Point:** HyperGraph serves as crystallization layer for knowledge generated across sessions, enabling semantic querying and emergent structure discovery

## ARCHITECTURE OVERVIEW

```
SESSION KNOWLEDGE GENERATION
├─ Conversations (user ↔ Claude)
├─ Code modifications
├─ Documentation created
├─ Reasoning traces
└─ State changes
    ↓
FUNCTOR AGENT (Bidirectional Translator)
├─ Human Format Generator
│  • Narrative structure
│  • Visual aids
│  • Examples
│  • Explanations
├─ LLM Format Generator
│  • Dense info
│  • Exact references
│  • Executable commands
│  • Structured data
└─ Metadata Extractor
   • Concepts
   • Relations
   • Dependencies
   • Context tags
    ↓
HYPERGRAPH (Knowledge Crystallization)
├─ Nodes: Concepts, Files, Systems, Views
├─ HyperEdges: N-dimensional relations
├─ Attributes: Flexible metadata (Dict[str, Any])
├─ Ontology: Dynamic, self-expanding
└─ Structure: Emergent, self-organized
    ↓
MULTI-ANGULAR VIEWS
├─ Architectural: System structure
├─ Operational: Usage patterns
├─ Integration: Cross-component links
├─ Debugging: Error patterns
├─ Historical: Design decisions
├─ Semantic: Concept relationships
└─ (N more views as needed)
    ↓
CONTEXT INJECTOR
├─ Query analysis
├─ Relevant layer selection
├─ Context assembly
└─ Transparent injection
    ↓
NEXT REQUEST (with optimal context)
```

## THEORETICAL FOUNDATIONS

### Category Theory
**Purpose:** Formal structure for knowledge representation

**Key Concepts:**
- Objects: Nodes in hypergraph (concepts, entities, systems)
- Morphisms: Relations between objects (edges, transformations)
- Functors: Structure-preserving maps between categories (format translation)
- Composition: Transitive relations (A→B, B→C ⟹ A→C)
- Universal constructions: Optimal solutions to mapping problems

**Application:**
```python
# Functor F: Human → LLM
F(knowledge_human) = knowledge_llm
F preserves structure: relations in human doc → relations in LLM doc

# Natural transformation η: F → G (between two functors)
η: HumanFormat → LLMFormat
η: LLMFormat → HumanFormat
```

### Complexity Theory
**Purpose:** Self-organization and emergent behavior

**Key Concepts:**
- Decentralized interactions: No central orchestrator
- Local rules: Simple agent behaviors
- Feedback loops: System state influences next actions
- Emergence: Complex patterns from simple iterations
- Attractors: Stable configurations (crystalline structures)

**Application:**
```python
# Iterative knowledge crystallization
while session_active:
    knowledge_chunk = agent.reason()
    subgraph = extract_reasoning_trace(knowledge_chunk)
    hypergraph.integrate(subgraph)  # Local operation
    # Emergent: Global structure organizes itself
    # No central planner dictates graph topology
```

### Self-Organization (Crystallization Metaphor)
**Natural Process:**
```
Water drips → Atoms arrange → Lattice forms → Crystal grows
```

**Knowledge Process:**
```
Agent reasons → Concepts link → Patterns emerge → Knowledge crystallizes
```

**Properties:**
- No predefined schema
- Structure emerges from content
- Stable configurations self-select
- Growth is organic, not programmed

## HYPERGRAPH STRUCTURE

### Core Data Model

```python
class Node:
    id: str
    type: str  # Concept, File, System, View, etc.
    attributes: Dict[str, Any]  # Flexible metadata

class Edge:
    id: str
    source: str
    target: str
    attributes: Dict[str, Any]

class HyperEdge:
    id: str
    nodes: List[str]  # N-dimensional relation
    relation_type: str  # Dynamic
    attributes: Dict[str, Any]

class RelationNode(Node):
    """Polymorphic relation node for flexible ontology"""
    relation_type: str

    def get_related_nodes(self) -> List[Node]
    def add_related_node(self, node: Node)
    def remove_related_node(self, node: Node)
```

### Example Knowledge Graph

```
Node("SISTEMA_SELECCION_PROYECTOS", type="System")
│
├─ HyperEdge("documented_as", nodes=[
│     Node("SISTEMA_SELECCION_PROYECTOS.md", type="HumanDoc"),
│     Node("SYSTEM_PROJECT_SELECTION_LLM.md", type="LLMDoc")
│   ])
│
├─ HyperEdge("implements", nodes=[
│     Node("enhanced_session_menu.py:27", type="Class"),
│     Node("project_context_manager.py:16", type="Class"),
│     Node("retro_launcher.py:80", type="Class")
│   ])
│
├─ HyperEdge("integrates_with", nodes=[
│     Node("FASE_1_NAVEGACION", type="System"),
│     Node("FASE_2_OUTPUT_STYLES", type="System"),
│     Node("FASE_3_CONTEXT_MANAGEMENT", type="System")
│   ])
│
├─ HyperEdge("stores_data_in", nodes=[
│     Node("~/.claude/data/projects.db", type="Database")
│   ])
│
└─ HyperEdge("viewed_from", nodes=[
│     Node("vista_arquitectural", type="View", content="..."),
│     Node("vista_operacional", type="View", content="..."),
│     Node("vista_debugging", type="View", content="...")
│   ])
```

## DUAL-FORMAT DOCUMENTATION

### Format Comparison

| Aspect | Human Format | LLM Format |
|--------|-------------|------------|
| Purpose | Cognitive comprehension | Inference efficiency |
| Structure | Narrative, sequential | Hierarchical, reference-dense |
| Visual | Emojis, diagrams, boxes | ASCII trees, tables |
| Examples | Step-by-step walkthroughs | Executable commands |
| Density | 40-60% explanatory text | 80-90% technical data |
| References | Relative (section names) | Absolute (file:line) |
| Token ratio | 1.0x baseline | 0.4-0.6x (40-60% reduction) |

### Functor Implementation Pattern

```python
class KnowledgeFunctor:
    """Bidirectional translator between formats"""

    def to_human(self, knowledge: Knowledge) -> HumanDoc:
        """F: Knowledge → HumanFormat"""
        return HumanDoc(
            narrative=self._generate_narrative(knowledge),
            examples=self._create_examples(knowledge),
            visuals=self._add_visual_aids(knowledge),
            explanations=self._expand_concepts(knowledge)
        )

    def to_llm(self, knowledge: Knowledge) -> LLMDoc:
        """F: Knowledge → LLMFormat"""
        return LLMDoc(
            structure=self._extract_structure(knowledge),
            references=self._make_absolute_refs(knowledge),
            commands=self._create_executables(knowledge),
            data=self._compress_info(knowledge)
        )

    def preserve_structure(self, knowledge: Knowledge) -> bool:
        """Verify F preserves relational structure"""
        human = self.to_human(knowledge)
        llm = self.to_llm(knowledge)
        return self._relations(human) == self._relations(llm)
```

## MULTI-ANGULAR VIEWS

### View Types

**1. Architectural View**
- System components
- Module boundaries
- Class hierarchies
- Data flow
- Dependency graph

**2. Operational View**
- Usage patterns
- Command sequences
- User workflows
- CLI interactions
- Menu navigation

**3. Integration View**
- Cross-component links
- API boundaries
- Hook activation points
- Database access patterns
- State file modifications

**4. Debugging View**
- Error patterns
- Bug fix history
- Known issues
- Troubleshooting paths
- Test failure patterns

**5. Historical View**
- Design decisions
- Evolution timeline
- Refactoring history
- Deprecated approaches
- Rationale documentation

**6. Semantic View**
- Concept relationships
- Domain terminology
- Ontology structure
- Knowledge clusters
- Reasoning patterns

### View Storage in HyperGraph

```python
Node("SISTEMA_SELECCION_PROYECTOS", type="System")
└─ HyperEdge("has_view", nodes=[
    Node("view_arch", type="View",
         content="""
         Components:
         - enhanced_session_menu.py:27 EnhancedSessionMenu
         - project_context_manager.py:16 ProjectContextManager
         - retro_launcher.py:80 ClaudeSupervisor

         Relationships:
         - Supervisor creates Menu
         - Menu queries ContextManager
         - ContextManager reads Database
         """),

    Node("view_operational", type="View",
         content="""
         User Flow:
         1. $ retro
         2. Menu: [1] Resume | [2] Select | [3] Fresh
         3. User: 2
         4. Menu: [1] navio | [2] astilleros | ...
         5. User: 1
         6. Menu: [1] Resume | [2] Fresh
         7. User: 1
         8. Claude starts in ~/navio_retro with --continue
         """),

    Node("view_integration", type="View",
         content="""
         Integration Points:
         - retro_launcher.py:354-361: os.chdir(project_path)
         - enhanced_session_menu.py:283: SELECT * FROM projects
         - output_style_switcher.py:67: _get_style_from_db()
         - intelligent_project_navigator.py: runtime navigation

         Hooks Activated:
         - session_initialization.py: context injection
         - project_context_loader.py: project metadata
         - meta_conversation_analyzer.py: intent detection
         """)
])
```

## CONTEXT INJECTION STRATEGY

### Layer Selection Algorithm

```python
def select_context_layers(user_query: str,
                          session_state: SessionState,
                          hypergraph: HyperGraph) -> List[Layer]:
    """
    Determine which context layers to inject for optimal response
    """
    layers = []

    # 1. Keyword analysis
    keywords = extract_keywords(user_query)

    # 2. Semantic search in hypergraph
    relevant_nodes = hypergraph.query(
        f"MATCH (n)-[:relates_to*1..3]->(k:Keyword) "
        f"WHERE k.text IN {keywords} "
        f"RETURN n, score(n) ORDER BY score DESC LIMIT 10"
    )

    # 3. View selection based on intent
    if is_debugging_query(user_query):
        layers.append(get_view(relevant_nodes, "debugging"))

    if is_implementation_query(user_query):
        layers.append(get_view(relevant_nodes, "architectural"))
        layers.append(get_view(relevant_nodes, "integration"))

    if is_usage_query(user_query):
        layers.append(get_view(relevant_nodes, "operational"))

    # 4. Historical context if asking "why"
    if contains_why(user_query):
        layers.append(get_view(relevant_nodes, "historical"))

    # 5. Project context
    if session_state.current_project:
        layers.append(get_project_context(session_state.current_project))

    # 6. Format selection
    if session_state.requester == "human":
        layers = [functor.to_human(layer) for layer in layers]
    else:  # LLM-to-LLM communication
        layers = [functor.to_llm(layer) for layer in layers]

    return layers

def inject_context(base_request: Request, layers: List[Layer]) -> Request:
    """Transparently inject selected layers"""
    return Request(
        user_message=base_request.user_message,
        system_context=build_context_string(layers),
        metadata={"injected_layers": [l.name for l in layers]}
    )
```

### Example Injection

**User Query:** "How do I add a new project to the selector?"

**Layer Selection:**
```python
layers = [
    get_view("SISTEMA_SELECCION_PROYECTOS", "operational"),  # Shows user flow
    get_view("SISTEMA_SELECCION_PROYECTOS", "architectural"),  # Shows ProjectContextManager
    get_code("project_context_manager.py", methods=["detect_project", "register_project"])
]
```

**Injected Context:**
```
OPERATIONAL VIEW:
User can add project via:
- Menu option 5: "Add new project (auto-detect)"
- enhanced_session_menu.py:244 handle_add_new_project()

ARCHITECTURAL VIEW:
ProjectContextManager.detect_project(directory)
  ├─ _find_git_root() # Line 102
  ├─ _analyze_git_project() # Line 111
  └─ _create_generic_project() # Line 100

CODE REFERENCE:
project_context_manager.py:80-100
def detect_project(self, directory: str) -> Optional[Dict]:
    # Auto-detection logic
    ...
```

## ISAAC'S MEMORY ENHANCEMENT

### Current System (FASE 3)

**File:** isaac_unified_memory.jsonl
**Format:** Append-only JSON lines
**Dimensions:** 2D (time, content)

```json
{"timestamp": "2025-09-30T01:00:00", "content": "Implemented selector...", "project": "navio"}
{"timestamp": "2025-09-30T01:15:00", "content": "Fixed import bug...", "project": "navio"}
```

**Limitations:**
- Linear structure
- Difficult semantic queries
- No relationship tracking
- Limited context retrieval

### Enhanced System (with HyperGraph)

**Storage:** HyperGraph nodes
**Format:** N-dimensional semantic graph
**Dimensions:** 5D+ (time, space, semantic, relational, contextual)

```python
# Isaac's memory as hypergraph
Node("memory_20250930_010000", type="IsaacMemory")
│
├─ HyperEdge("occurred_at", nodes=[
│     Node("2025-09-30T01:00:00", type="Timestamp")
│   ])
│
├─ HyperEdge("occurred_in", nodes=[
│     Node("navio_retro", type="Project"),
│     Node("~/navio_retro", type="Directory")
│   ])
│
├─ HyperEdge("about_concept", nodes=[
│     Node("project_selection", type="Concept"),
│     Node("database_integration", type="Concept"),
│     Node("bug_fix", type="Concept")
│   ])
│
├─ HyperEdge("relates_to", nodes=[
│     Node("SISTEMA_SELECCION_PROYECTOS", type="System"),
│     Node("enhanced_session_menu.py", type="File")
│   ])
│
├─ HyperEdge("has_purpose", nodes=[
│     Node("fix_import_error", type="Goal"),
│     Node("enable_menu_display", type="Goal")
│   ])
│
└─ HyperEdge("has_outcome", nodes=[
      Node("import_fixed", type="Result"),
      Node("tests_passed", type="Result")
    ])
```

**Queries Enabled:**

```cypher
# All memories about navigation
MATCH (m:IsaacMemory)-[:about_concept]->(c:Concept {name: "navigation"})
RETURN m ORDER BY m.timestamp DESC

# Memories from visits to astilleros
MATCH (m:IsaacMemory)-[:occurred_in]->(p:Project {name: "astilleros_retro"})
RETURN m

# Bug fixes related to database
MATCH (m:IsaacMemory)-[:about_concept]->(c {name: "bug_fix"})
MATCH (m)-[:relates_to]->(s)-[:uses]->(db:Database)
RETURN m, s, db

# Cross-project patterns
MATCH (m1:IsaacMemory)-[:occurred_in]->(p1:Project)
MATCH (m2:IsaacMemory)-[:occurred_in]->(p2:Project)
WHERE m1.content SIMILAR_TO m2.content AND p1 != p2
RETURN p1, p2, similarity_score(m1, m2)

# Temporal patterns (what happened after X)
MATCH (m1:IsaacMemory)-[:occurred_at]->(t1:Timestamp)
MATCH (m2:IsaacMemory)-[:occurred_at]->(t2:Timestamp)
WHERE t2.value > t1.value AND t2.value < t1.value + timedelta(hours=1)
MATCH (m1)-[:relates_to]->(s:System)
MATCH (m2)-[:relates_to]->(s)
RETURN m1, m2, s  # Events on same system within 1 hour
```

## IMPLEMENTATION ROADMAP

### Phase 1: Core HyperGraph (Estimated: 2-3 weeks)

**Iteration 1.1: Base Model + InMemory Repository**
```python
# Files to create:
~/hypergraph/
├── src/
│   ├── core/
│   │   ├── node.py          # Node, Edge, HyperEdge classes
│   │   ├── hypergraph.py    # HyperGraph container
│   │   └── repository.py    # HypergraphRepository interface
│   ├── repositories/
│   │   ├── memory.py        # InMemoryHypergraphRepository
│   │   └── json_file.py     # JsonFileHypergraphRepository
│   └── __init__.py
├── tests/
│   ├── test_node.py
│   ├── test_hypergraph.py
│   └── test_repository.py
└── pyproject.toml
```

**Iteration 1.2: CRUD Commands**
```python
# Files to create:
~/hypergraph/src/
├── commands/
│   ├── add_node.py          # AddNodeCommand, AddNodeHandler
│   ├── update_node.py       # UpdateNodeCommand, UpdateNodeHandler
│   ├── remove_node.py       # RemoveNodeCommand, RemoveNodeHandler
│   └── get_node.py          # GetNodeCommand, GetNodeHandler
└── command_bus.py           # CommandBus dispatcher
```

**Iteration 1.3: JSON Persistence**
```python
# Implement:
# - JsonFileHypergraphRepository.save()
# - JsonFileHypergraphRepository.load()
# - Versioningand schema evolution
```

### Phase 2: Dynamic Ontologies (Estimated: 2-3 weeks)

**Iteration 2.1: Flexible Attributes**
```python
class Node:
    id: str
    type: str
    attributes: Dict[str, Any]  # Add this

# Support arbitrary metadata
node = Node(id="doc1", type="Document",
            attributes={
                "format": "markdown",
                "token_count": 1500,
                "created_at": "2025-09-30",
                "tags": ["llm-optimized", "technical"]
            })
```

**Iteration 2.2: Relation Nodes**
```python
class RelationNode(Node):
    relation_type: str

    def get_related_nodes(self) -> List[Node]:
        """Traverse hypergraph to find connected nodes"""

    def add_related_node(self, node: Node):
        """Create new hyperedge to node"""

    def remove_related_node(self, node: Node):
        """Remove hyperedge to node"""

# Usage:
implements = RelationNode(
    id="rel1",
    type="Relation",
    relation_type="implements"
)
implements.add_related_node(system_node)
implements.add_related_node(class_node)
implements.add_related_node(function_node)
```

### Phase 3: LLM Integration (Estimated: 3-4 weeks)

**Iteration 3.1: Query with LLM**
```python
# File: ~/hypergraph/src/llm/
├── query_handler.py
├── prompt_manager.py
└── llm_client.py

# Flow:
user_query → QueryHypergraphHandler
  → retrieves relevant graph data
  → builds contextualized prompt
  → sends to LLM
  → returns LLM response
```

**Iteration 3.2: Extract Commands from LLM**
```python
# File: ~/hypergraph/src/llm/parser.py

class LLMResponseParser:
    """Parse commands from LLM responses"""

    def parse(self, llm_response: str) -> List[Command]:
        """
        Extract commands from response
        Format: [ADD_NODE id=X type=Y attr1=Z]
        """
        commands = []
        for match in re.finditer(r'\[([A-Z_]+)\s+(.*?)\]', llm_response):
            cmd_type = match.group(1)
            args = self._parse_args(match.group(2))
            commands.append(self._create_command(cmd_type, args))
        return commands
```

**Iteration 3.3: Semantic Validation**
```python
# File: ~/hypergraph/src/ontology/validator.py

class OntologyValidator:
    """Validate commands against dynamic ontology"""

    def validate(self, command: Command, hypergraph: HyperGraph) -> bool:
        """
        Check if command is valid given current ontology
        - Type consistency
        - Attribute validity
        - Relation constraints
        """
```

### Phase 4: Functor Implementation (Estimated: 2 weeks)

```python
# File: ~/hypergraph/src/functor/
├── knowledge_functor.py
├── human_formatter.py
└── llm_formatter.py

class KnowledgeFunctor:
    def to_human(self, knowledge: Knowledge) -> HumanDoc
    def to_llm(self, knowledge: Knowledge) -> LLMDoc
    def preserve_structure(self, k: Knowledge) -> bool
```

### Phase 5: Retro Integration (Estimated: 1-2 weeks)

```python
# Files to create/modify:
~/.claude/tools/
├── knowledge_crystallizer.py    # NEW: Converts session → hypergraph
├── context_layer_injector.py    # NEW: Injects layers into requests
└── multi_angle_documenter.py    # NEW: Generates multi-view docs

~/.claude/hooks/
└── knowledge_capture_hook.py    # NEW: Captures knowledge during session

# Modifications:
~/.claude/tools/project_context_manager.py  # Add hypergraph integration
~/navio_retro/docs/isaac_marinero_output_style.md  # Update with hypergraph memory
```

## FILE STRUCTURE

```
~/hypergraph/                                    # Main project directory
├── src/
│   ├── core/
│   │   ├── node.py                             # Node, Edge, HyperEdge
│   │   ├── hypergraph.py                       # HyperGraph container
│   │   └── repository.py                       # Repository interface
│   ├── repositories/
│   │   ├── memory.py                           # In-memory implementation
│   │   ├── json_file.py                        # JSON persistence
│   │   └── neo4j.py                            # Future: Neo4j backend
│   ├── commands/
│   │   ├── command_bus.py                      # Command dispatcher
│   │   ├── add_node.py
│   │   ├── update_node.py
│   │   ├── remove_node.py
│   │   └── query.py
│   ├── ontology/
│   │   ├── manager.py                          # OntologyManager
│   │   ├── validator.py                        # OntologyValidator
│   │   └── relation_node.py                    # RelationNode class
│   ├── llm/
│   │   ├── query_handler.py
│   │   ├── parser.py                           # LLMResponseParser
│   │   ├── prompt_manager.py
│   │   └── llm_client.py
│   ├── functor/
│   │   ├── knowledge_functor.py                # Main functor
│   │   ├── human_formatter.py
│   │   └── llm_formatter.py
│   └── __init__.py
├── tests/
│   ├── test_core.py
│   ├── test_commands.py
│   ├── test_ontology.py
│   ├── test_llm.py
│   └── test_functor.py
├── docs/
│   ├── architecture.md                         # Human format
│   ├── architecture_llm.md                     # LLM format
│   └── examples/
│       ├── basic_usage.py
│       └── integration_retro.py
├── pyproject.toml
├── README.md
└── .gitignore

~/.claude/                                       # Retro Framework integration
├── tools/
│   ├── knowledge_crystallizer.py              # Session → HyperGraph
│   ├── context_layer_injector.py              # Layer injection
│   └── multi_angle_documenter.py              # Multi-view generation
├── hooks/
│   └── knowledge_capture_hook.py              # Automatic capture
├── data/
│   ├── hypergraph.json                        # Knowledge graph storage
│   └── projects.db                            # Existing projects DB
└── docs/
    └── HYPERGRAPH_MULTICONTEXT_SYSTEM_LLM.md  # This document
```

## INTEGRATION WITH EXISTING SYSTEMS

### With FASE 1 (Intelligent Navigation)

**Flow:**
```
User: "vamos a astilleros"
  ↓
meta_conversation_analyzer detects intent
  ↓
intelligent_project_navigator executes
  ↓
HYPERGRAPH CAPTURES:
  Node("navigation_event_20250930")
    ├─ occurred_at: timestamp
    ├─ from_project: navio_retro
    ├─ to_project: astilleros_retro
    ├─ trigger: "vamos a astilleros"
    └─ method: meta_analyzer_detection
  ↓
Future queries can find:
  "How many times have we visited astilleros?"
  "What were we doing before visiting astilleros?"
  "Which projects do we visit most?"
```

### With FASE 2 (Output Style Switcher)

**Flow:**
```
Project change triggered
  ↓
output_style_switcher consults DB
  ↓
Style loaded (e.g., "Isaac Marinero")
  ↓
HYPERGRAPH CAPTURES:
  Node("style_switch_20250930")
    ├─ occurred_at: timestamp
    ├─ project: navio_retro
    ├─ from_style: null
    ├─ to_style: "Isaac Marinero"
    └─ reason: "project_context"

  HyperEdge("uses_style", nodes=[
    Node("navio_retro"),
    Node("Isaac Marinero")
  ])
  ↓
Future queries:
  "Which style is used in navio?"
  "When did we last use Boris Vian style?"
  "Which projects share the same style?"
```

### With FASE 3 (Context Management - Isaac)

**Flow:**
```
Isaac listens during visit to astilleros
  ↓
Conversation captured in isaac_listening_log.jsonl
  ↓
When returning home:
  ↓
HYPERGRAPH INTEGRATION:
  For each exchange in listening_log:
    Node("isaac_memory_X")
      ├─ content: exchange
      ├─ occurred_in: astilleros_retro
      ├─ context: "visit"
      ├─ concepts: [extracted concepts]
      └─ relations: [to systems, files, tasks]
  ↓
Isaac can now query:
  "What did Don Álvaro say about the gift?"
  "Which optimizations were discussed at astilleros?"
  "Show me all conversations about maintenance"
```

## QUERY LANGUAGE

### Cypher-like Syntax

```cypher
# Find all documentation for a system
MATCH (sys:System {name: "SELECCION_PROYECTOS"})-[:documented_as]->(doc)
RETURN doc

# Find code that implements a concept
MATCH (concept:Concept {name: "navigation"})<-[:implements]-(code:File)
RETURN code.path, code.line

# Find related systems
MATCH (sys1:System)-[:integrates_with]-(sys2:System)
WHERE sys1.name = "FASE_2"
RETURN sys2

# Temporal queries
MATCH (m:IsaacMemory)-[:occurred_at]->(t:Timestamp)
WHERE t.value > '2025-09-30'
RETURN m ORDER BY t.value

# Semantic similarity
MATCH (n1)-[:about_concept]->(c)
MATCH (n2)-[:about_concept]->(c)
WHERE n1 != n2
RETURN n1, n2, c

# Path finding
MATCH path = (start:System {name: "FASE_1"})
             -[:relates_to*1..5]->
             (end:System {name: "FASE_3"})
RETURN path ORDER BY length(path) LIMIT 1
```

### Python API

```python
from hypergraph import HyperGraph

hg = HyperGraph.load("~/.claude/data/hypergraph.json")

# Simple queries
system = hg.get_node("SISTEMA_SELECCION_PROYECTOS")
docs = hg.get_related(system, relation="documented_as")

# Complex queries
results = hg.query("""
    MATCH (m:IsaacMemory)-[:about_concept]->(c:Concept)
    WHERE c.name IN ['navigation', 'database']
    RETURN m, c
""")

# Semantic search
similar = hg.semantic_search("How to add project to selector?", top_k=5)

# Graph algorithms
clusters = hg.find_clusters(algorithm="louvain")
centrality = hg.compute_centrality(algorithm="pagerank")
```

## PERFORMANCE CONSIDERATIONS

**Graph Size Estimates:**
- 1 session = ~50-200 nodes (concepts, files, events)
- 100 sessions = ~5,000-20,000 nodes
- 1000 sessions = ~50,000-200,000 nodes

**Query Performance:**
- In-memory: O(1) node access, O(E) traversal
- JSON file: O(N) load time, then in-memory
- Neo4j: O(log N) indexed access, efficient traversals

**Optimization Strategies:**
- Batch insertions during session
- Periodic graph compaction (merge similar nodes)
- Lazy loading of subgraphs
- Query result caching
- Indexing on frequently queried attributes

## METRICS & MONITORING

**Knowledge Crystallization Metrics:**
- Nodes added per session
- Edges created per session
- Graph density (edges/nodes)
- Cluster coefficient
- Average path length
- Emergent structure score

**Functor Metrics:**
- Translation time (human/LLM)
- Structure preservation score
- Information loss/gain
- Token compression ratio

**Context Injection Metrics:**
- Layers selected per query
- Injection time overhead
- Context relevance score
- User satisfaction (implicit)

## SECURITY & PRIVACY

**Considerations:**
- Sensitive information in graph nodes
- Query access control
- Graph export restrictions
- Memory pruning (Isaac's selective forgetting)
- Encryption at rest
- Audit logging for graph modifications

**Implementation:**
```python
class SecureHyperGraph(HyperGraph):
    def __init__(self, access_control: AccessControl):
        self.acl = access_control

    def get_node(self, node_id: str, user: User) -> Optional[Node]:
        if not self.acl.can_read(user, node_id):
            raise PermissionError
        return super().get_node(node_id)

    def add_node(self, node: Node, user: User) -> str:
        if not self.acl.can_write(user):
            raise PermissionError
        if node.is_sensitive():
            node = self._encrypt(node)
        return super().add_node(node)
```

## REFERENCES

**Theoretical:**
- MIT Research Paper: "Emergent Intelligence from Simple Iterations"
- Category Theory: Mac Lane, "Categories for the Working Mathematician"
- Complexity Theory: Mitchell, "Complexity: A Guided Tour"
- Knowledge Graphs: Hogan et al., "Knowledge Graphs" (ACM Survey)

**Implementation:**
- NetworkX: Python graph library
- Neo4j: Graph database
- RDFLib: Semantic web toolkit
- LangChain: LLM integration patterns

**Related Systems:**
- FASE 1: ~/navio_retro/docs/INFORME_FASE_1_NAVEGACION_COMPLETA.md
- FASE 2: ~/navio_retro/docs/INFORME_FASE_2_OUTPUT_STYLES.md
- FASE 3: ~/navio_retro/docs/INFORME_FASE_3_CONTEXT_MANAGEMENT.md
- Project Selection: ~/.claude/docs/SYSTEM_PROJECT_SELECTION_LLM.md

## STATUS SUMMARY

**Current State:**
- Conceptual design: COMPLETE
- Directory structure: EMPTY (~hypergraph, ~/infrastructure/graph_functions)
- Conversation docs: EXISTS (~/downloads/Local 1 - Gemini conversation JSON)
- Integration points: IDENTIFIED
- Theoretical foundation: DOCUMENTED

**Next Steps:**
1. Create ~/hypergraph project structure
2. Register hypergraph in Retro projects DB
3. Implement Phase 1.1: Base model + InMemory repository
4. Write unit tests for core classes
5. Implement Phase 1.2: CRUD commands
6. Integrate with first Retro system (project selection)

**Decision Point:** Awaiting user confirmation to proceed with implementation

**Date:** 2025-09-30
**Documented by:** Isaac - Marinero del Navío Retro
**Format:** LLM-optimized technical reference