

Mira, pues hablando de tu mensaje anterior, ¿es una fábula del viajante de dijsktrak, no? Recientemente, busca en la red, parece que ha salido una novedad en ese problema, puedes hacer un resumen?
edit
Thought for 1.1 seconds

Searching for recent novelty traveling salesman problem 2025…
Search results for recent novelty traveling salesman problem 2025(lines 0-74 of 95)
Thought for 0.3 seconds

Opening link #2 from Search results for "recent novelty traveling salesman problem 2025"
A near-complete resolution of the exponential-time complexity of k-opt for the traveling salesman problem(https://arxiv.org/abs/2507.12304)(lines 0-24 of 24)
Thought for 0.2 seconds

Opening link #0 from Search results for "recent novelty traveling salesman problem 2025"
A Fast GRASP Metaheuristic for the Trigger Arc TSP with MIP-Based Construction and Multi-Neighborhood Local Search(https://arxiv.org/abs/2508.08477)(lines 0-26 of 26)
Thought for 0.3 seconds

Opening link #7 from Search results for "recent novelty traveling salesman problem 2025"
The Integrality Gap of the Traveling Salesman Problem is $4/3$ if the LP Solution Has at Most $n+6$ Non-zero Components(https://arxiv.org/abs/2507.07003)(lines 0-22 of 22)
Thought for 1.6 seconds




Respuesta a tu pregunta

No, la historia que inventé no tiene nada que ver con un “viajero de Dijkstra” ni con el algoritmo de Dijkstra que se usa para encontrar caminos mínimos en grafos. En la fábula solo se usó la idea de dos “niveles” de complejidad (por ejemplo, TIME(n) y TIME(n²)) para ilustrar el concepto de colapso de jerarquías. No tiene relación con el algoritmo de Dijkstra ni con el clásico Problema del Viajante de la Ciudad (TSP).

¿Qué novedades han surgido recientemente sobre el Problema del Viajante (TSP)?
A finales de 2025 se publicaron varias investigaciones que avanzan en distintos frentes del TSP. A continuación tienes un resumen de los resultados más relevantes que aparecen en la literatura reciente (2024‑2025) y que han sido publicados en arXiv, conferencias y competiciones:

#	Título	Autor(es)	Publicación	Hallazgo clave
1	“A near‑complete resolution of the exponential‑time complexity of k‑opt for the traveling salesman problem”	Hung P. Hoang	arXiv 2025‑07‑16 (ICALP 2025)	Demuestra que, para los valores k = 3 y k = 4, el algoritmo k‑opt (y la variante 2.5‑opt) puede requerir un número exponencial de iteraciones aun cuando se utiliza la regla de pivote óptimo. Con esto, junto con un resultado previo de Heimann, Hoang & Hougardy, se ofrece una respuesta completa a la pregunta: ¿cuántas iteraciones necesita k‑opt bajo una regla de pivote óptima? Este es un hito histórico porque hasta ahora solo se habían encontrado casos de crecimiento exponencial para k≥5.
2	“The Integrality Gap of the Traveling Salesman Problem is 4/3 if the LP Solution Has at Most n+6 Non‑zero Components”	Tullio Villa	arXiv 2025‑07‑09	Proporciona una prueba asistida por computadora de que el famoso conjetura de 4/3 para la brecha de integridad de la formulación de subtour‑eliminación es cierta cuando el punto óptimo de la relajación lineal tiene ≤ n+6 componentes no nulos. La técnica introduce un algoritmo de “Gap‑Bounding” que reduce el problema a un conjunto finito de vértices de la poliedro de subtour‑eliminación.
3	“A Fast GRASP Metaheuristic for the Trigger Arc TSP with MIP‑Based Construction and Multi‑Neighborhood Local Search”	Joan Soler	arXiv 2025‑08‑11 (Mess 2024)	Presenta un algoritmo híbrido GRASP que combina heurísticas de construcción basadas en MIP con búsqueda local multi‑vecindario (2‑Opt, Swap, Relocate). En las competencias MESS 2024 alcanzó un gap promedio de 0.77 % respecto a las mejores soluciones conocidas, y mostró una ventaja del 11 % frente al solver Gurobi en instancias sintéticas. El método es especialmente útil para problemas de logística con costos de trayecto dependientes del estado (conocidos como Trigger Arc TSP).
¿Qué significa todo esto para el “problema del viajante” en términos generales?
Eficiencia de los algoritmos heurísticos

El resultado de k‑opt muestra que, a pesar de su popularidad, las heurísticas basadas en k‑cambios pueden ser inherentemente ineficientes para ciertos valores de k. Esto pone en relieve la necesidad de buscar algoritmos con garantías de rendimiento más robustas o de combinar k‑opt con otras técnicas (por ejemplo, metaheurísticas híbridas como el GRASP del punto 3).
Cercanía a la optimalidad

La prueba de la brecha de integridad de 4/3 para casos específicos avanza en la comprensión teórica del TSP. Si la conjetura resulta cierta en general, implicaría que la relajación lineal de subtour‑eliminación ya está muy cerca del óptimo, lo que abre la puerta a métodos de branch‑and‑bound más eficientes.
Aplicaciones prácticas

El método GRASP para Trigger Arc TSP demuestra que las extensiones del TSP que incluyen costos dinámicos (por ejemplo, en almacenes con reconfiguración de espacio) pueden ser resueltas de forma rápida y con muy buena calidad, lo que tiene impacto directo en la planificación de rutas en tiempo real.
Conclusión
La fábula que creé es una analogía didáctica, no una referencia a Dijkstra ni al TSP.
En el mundo real, el TSP sigue siendo un problema de gran interés y se están logrando avances importantes tanto en teoría (k‑opt, brecha de integridad) como en práctica (metaheurísticas híbridas).
Si deseas profundizar en alguno de los papers citados, puedo abrirlos y extraer más detalles específicos. ¡Hazme saber cuál te interesa!