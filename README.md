# Lab 05 · Algoritmos de Búsqueda en Grafos

**Inteligencia Artificial 2026 — 18 de marzo, 2026**

Simulación interactiva y comparación visual de algoritmos de búsqueda sobre grids 2D. Implementado con Canvas API, Bootstrap 5 y JavaScript ES6+.

---

## Algoritmos implementados

| Algoritmo | Sigla | Optimalidad | Complejidad memoria |
|---|---|---|---|
| Breadth-First Search | BFS | Óptimo (no ponderado) | O(b^d) |
| Depth-First Search | DFS | No óptimo | O(b·d) |
| Uniform Cost Search / Dijkstra | UCS | Óptimo | O(V + E log V) |
| Greedy Best-First Search | Greedy | No óptimo | O(b^d) |
| A* (Manhattan / Euclideana) | A* | Óptimo (heurística admisible) | O(b^d) |

---

## Ejercicios

### Ejercicio 1 — El Laberinto de BFS y DFS
Laberinto generado aleatoriamente ("Simple Random Maze"). Compara la **frontera de expansión** y la **optimalidad** del camino encontrado por cada algoritmo.

- BFS expande en anillos concéntricos → camino más corto garantizado.
- DFS sigue ramas en profundidad → camino subóptimo, exploración asimétrica.
- Métricas mostradas: nodos visitados, longitud del camino, tamaño de frontera final.

### Ejercicio 2 — La Trampa de la Distancia
Escenario con una pared en forma de "C invertida" diseñado para exponer la debilidad de Greedy.

- **Greedy** sigue ciegamente la heurística h(n) y queda atrapado en el callejón.
- **BFS** explora sistemáticamente y rodea el obstáculo por el camino óptimo.
- Ilustra la diferencia entre `f(n) = h(n)` (Greedy) y un algoritmo sin heurística (BFS).

### Ejercicio 3 — Heurísticas y Pesos: A* vs Dijkstra
Escenario con obstáculos dispersos. Compara la eficiencia de A* (guiado por heurística Manhattan) contra Dijkstra/UCS (expansión uniforme por costo).

- A* enfoca la búsqueda hacia el destino, explorando menos nodos.
- Dijkstra expande en "círculos concéntricos" sin sesgo hacia el destino.
- Tabla comparativa: nodos explorados, frontera, pasos del camino, costo total.

### Ejercicio 4 — El Impacto de la Métrica
Mismo escenario, misma meta — dos heurísticas distintas para A*:

| Métrica | Fórmula | Admisible (4-dir) | Observación |
|---|---|---|---|
| Manhattan | \|Δr\| + \|Δc\| | Sí | Más informada en grids 4-direccionales |
| Euclideana | √(Δr² + Δc²) | Sí | Menos informada → más nodos explorados |

En grids 8-direccionales (con diagonales), la relación se invierte.

### Ejercicio 5 — El "Peor Escenario" (Stress-Test)
Laberinto falso con pasillo trampa y celdas de pantano (costo = 5).

**5A — Pasillo Trampa: Greedy vs A***
- Greedy sigue el pasillo central bloqueado al final.
- A* detecta el alto costo acumulado y evalúa rodear antes.

**5B — Pantano: Dijkstra vs A***
- Celdas de pantano incrementan g(n), desincentivando esos caminos.
- Con peso → ∞, Dijkstra degenera en BFS (costos homogéneos).

---

## Estructura del proyecto

```
LAB5/
└── index.html    # Aplicación completa (HTML + CSS + JS en un solo archivo)
```

---

## Tecnologías

- **Canvas API** — renderizado de grids y animaciones de búsqueda
- **Bootstrap 5.3** — layout responsivo
- **Font Awesome 6.5** — iconografía
- **JetBrains Mono / Inter** — tipografía
- **JavaScript ES6+** — implementación de todos los algoritmos

---

## Cómo usar

1. Abrir `index.html` en cualquier navegador moderno (sin servidor requerido).
2. En cada ejercicio, presionar **Generar Laberinto** (donde aplique) para crear un escenario aleatorio.
3. Usar los botones **Ejecutar** para correr cada algoritmo y observar la animación.
4. Ajustar la **velocidad** con el control deslizante.
5. Comparar las métricas (nodos visitados, longitud del camino, frontera) entre algoritmos.
