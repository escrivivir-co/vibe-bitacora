¿Qué hace que este "grafo" sea válido?
--------------------------------------

Un diagrama de draw.io (también llamado *diagrams.net*) se describe en XML.\
Para que cualquiera pueda crear uno nuevo --o que un modelo de lenguaje (ex. tu agente) lo genere automáticamente-- es necesario seguir una serie de normas "internas" que los constructores de este XML imparten sin que nos demos cuenta.\
A continuación se resume cada una de esas reglas, con ejemplos concretos extraídos del *grafo* que has pegado.

* * * * *

1\. Estructura del documento
----------------------------

| Elemento | Que debe contener | Comentario de ejemplo |
| --- | --- | --- |
| `<mxfile ...>` | Recurso raíz. Los atributos `host`, `agent`, `version` suelen dejarse por defecto. | `host="app.diagrams.net" ... version="28.1.2"` |
| `<diagram ...>` | Una instancia del diagrama. Necesita un `name` y un `id` único. | `name="Page-1" id="nrMDSHrh1mtwg5gxZ5Ba"` |
| `<mxGraphModel ...>` | Contenedor que mantiene la configuración global (grid, guides, etc.) y la raíz (`<root>`). | `dx="1262" dy="947" ... pageWidth="827"` |
| `<root>` | Contiene todas las celdas (`mxCell`). Siempre empieza con dos celdas base: | `<mxCell id="0" /><mxCell id="1" parent="0" />` |

* * * * *

2\. Células (*mxCell*)
----------------------

### 2.1. Celdas de vertices (nodos)

```
<mxCell id="iC1rTaQaeNt96tmryydn-101" value="Orchestrator&lt;br&gt;(RxJS + NodeJS)" style="rounded=1;whiteSpace=wrap;html=1;fontSize=12;fontColor=#000000;strokeColor=#000000;fillColor=#FFFFFF;" vertex="1" parent="1">
  <mxGeometry x="740" y="1160" width="140" height="70" as="geometry" />
</mxCell>

```

Reglas

1.  `vertex="1"` ⇒ es un nodo.
2.  `parent="1"` ⇒ pertenece a la raíz.
3.  `id` debe ser único; habitualmente sigue un esquema `iC1rTaQaeNt96tmryydn-<n>`.
4.  `value` es el texto que aparece dentro del nodo. Cuando incluye `<br>` u otros caracteres "sangre", deben escaparse (`<` → `&lt;`, `>` → `&gt;`).
5.  `style` controla la apariencia:
    -   `rounded=1` -- bordes redondeados.
    -   `whiteSpace=wrap;html=1` -- permite formato HTML interno, necesario para `<br>`.
    -   `fillColor`, `strokeColor` -- colores.
6.  `<mxGeometry ...>` describe posición y tamaño: `x`, `y`, `width`, `height`.

### 2.2. Celdas de edges (conexiones)

```
<mxCell id="iC1rTaQaeNt96tmryydn-108" style="edgeStyle=orthogonalEdgeStyle;elbow=horizontal;strokeColor=#000000;dashed=1;" edge="1" parent="1" source="iC1rTaQaeNt96tmryydn-101" target="iC1rTaQaeNt96tmryydn-102">
  <mxGeometry relative="1" as="geometry">
    <mxPoint x="580" y="1230" as="targetPoint" />
  </mxGeometry>
</mxCell>

```

Reglas

1.  `edge="1"` ⇒ es una arista.
2.  `source="..." target="..."` ⇒ referencia a los ids de los nodos que conecta.
3.  `style` define la ruta de la flecha (`orthogonalEdgeStyle`, `elbow=horizontal`, `dashed=1`, etc.).
4.  `<mxGeometry relative="1">` indica que la geometría es relativa a la escena y, opcionalmente, se pueden usar puntos de "targetPoint"/"sourcePoint" o arrays de puntos para guiar la forma de la línea.

### 2.3. Celdas de texto (en sobres, mensajes, etiquetas)

```
<mxCell id="iC1rTaQaeNt96tmryydn-116" value="Runtime1 initialized" style="shape=mxgraph.signs.tech.mail;html=1;pointerEvents=1;fillColor=#FFFFFF;strokeColor=#000000;verticalLabelPosition=bottom;verticalAlign=top;align=center;sketch=0;" vertex="1" parent="1">
  <mxGeometry x="430" y="980" width="120" height="50" as="geometry" />
</mxCell>

```

Reglas

1.  `vertex="1"` (aunque sea una caja sin nodo conectado).
2.  `style` comienza con `shape=...` para usar iconos de la librería (por ejemplo `mxgraph.signs.tech.mail`).
3.  `html=1` permite texto con etiquetas HTML.
4.  El `value` puede incluir texto plano o con etiquetas, siempre escapadas.

* * * * *

3\. Evitar errores comunes
--------------------------

| Problema | Causa típica | Solución |
| --- | --- | --- |
| XML "rompe" al cargar | `<` o `>` sin escapar dentro de `value` | usar `&lt;` y `&gt;` |
| Texto sin saltos de línea | No usar `html=1` y `<br>` | Añadir `html=1` y `<br>` (escapado) |
| Nodo sin padre | Olvidar `parent="1"` | Incluir siempre `parent="1"` |
| Faltan aristas | Olvidar `edge="1"` o `source/target` | Añadir esos atributos |
| Estilos incoherentes | Mezclar formatos | Definir un `style="rounded=1;whiteSpace=wrap;html=1;..."` consistente |

* * * * *

4\. Plantilla de "prompt‐to‑XML"
--------------------------------

Para que un agente genere un diagrama nuevo, una receta de prompt muy útil es:

```
{
  "type": "svg-diagram",
  "title": "Mi Diagrama",
  "nodes": [
    {"id":"A","label":"Orchestrator (RxJS + NodeJS)","x":740,"y":1160,"w":140,"h":70,"color":"#FFFFFF","stroke":"#000000","style":"rounded=1;whiteSpace=wrap;html=1;fontSize=12;"},
    {"id":"B","label":"App (AppMessage)","x":380,"y":1170,"w":120,"h":50,"color":"#EBF5FB","stroke":"#0000FF","style":"rounded=1;whiteSpace=wrap;html=1;fontSize=11;"},
    ...
  ],
  "edges": [
    {"id":"E1","source":"A","target":"B","style":"edgeStyle=orthogonalEdgeStyle;elbow=horizontal;strokeColor=#000000;dashed=1;", "points":[{"x":580,"y":1230}]},
    ...
  ],
  "textboxes": [
    {"id":"M1","label":"Runtime1 initialized","x":430,"y":980,"w":120,"h":50,"shape":"mxgraph.signs.tech.mail","stroke":"#000000"},
    ...
  ]
}

```

Luego, tu agente puede convertir fielmente este JSON a XML siguiendo las reglas anteriores.

* * * * *

5\. Resumen rápido de "reglas de oro"
-------------------------------------

| Paso | Qué hacer | Qué evitar |
| --- | --- | --- |
| 1 | Empezar con `<mxfile>` → `<diagram>` → `<mxGraphModel>` → `<root>` | No saltar la jerarquía |
| 2 | Agregar `_0` y `_1` | Olvidar id "0" y "1" causa error |
| 3 | Crear nodos con `vertex="1"` | No dar `parent="1"` produce nodo órfano |
| 4 | Crear edges con `edge="1"` y `source/target` | Conectar con IDs inexistentes |
| 5 | Escapar `<` y `>` y usar `html=1` | Texto con `<br>` sin escapar rompe el XML |
| 6 | Usar geometría (`x`, `y`, `width`, `height`) en cada cell | Posición/size implícita puede romper layout |
| 7 | Estilos consistentes (`rounded=1;whiteSpace=wrap;html=1;...`) | Diferentes estilos pueden hacerle "diferido" la visualización |

Con estas reglas el agente "sabe" cómo construir un diagrama valioso: cada nodo, borde y texto es una celda bien formada, con identificadores únicos, geometría coherente y estilo legible.

¡Ya puedes compartir estos "códigos" a tu agente y dejar que genere nuevos diagramas sin romper la trama!

# 2\. Problemas comunes que se pueden encontrar (y cómo evitarlos)

| Problema | Causa | Solución |
| --- | --- | --- |
|  XML "rompe" al cargar | Se usan caracteres `<` y `>` directamente dentro de atributos `value`. | Escapar: `<` → `&lt;`, `>` → `&gt;`. |
|  Textos no se rompen en varias líneas | draw.io necesita HTML interno y la opción `html=1`. | Agregar `html=1` en el estilo y usar `<br>` (escapado) en `value`. |
|  Falta de celda base | El modelo necesita una celda padre (`id="0"`) y una referencia (`id="1"`). | Mantener `<mxCell id="0"/>` y `<mxCell id="1" parent="0"/>`. |
|  Faltan aristas (edges) | Se olvidó el atributo `edge="1"` y la conexión `source`/`target`. | Añadir `<mxCell id="..." edge="1" source="..." target="..." parent="1">...`. |
|  Formato visual incoherente | Estilos inconsistentes (rounded, fill, stroke). | Definir `style="rounded=1;whiteSpace=wrap;html=1;...;"` coherente en todas las celdas. |