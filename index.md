# Resolviendo un laberinto con A* en Unity

Trabajo de Inteligencia Artificial.

## Qué es A*:

A* es un algoritmo de búsqueda que encuentra el camino de menor coste entre un origen y un destino. 
A diferencia de BFS, que explora por niveles sin saber dónde está la meta, o DFS, que se interna en profundidad sin garantías de optimalidad,
A* usa información sobre el objetivo para dirigir la búsqueda.

Para cada nodo n calcula:

f(n) = g(n) + h(n)

- g(n): es el coste real recorrido desde el inicio hasta n.
- h(n): es la estimación del coste que falta hasta la meta. Aquí uso la distancia euclídea.
- f(n): es el coste total estimado de un camino que pase por n.

Si la heurística nunca sobreestima el coste real por lo tanto es admisible, A* garantiza el camino óptimo.

## Cómo lo he implementado

El proyecto parte de una escna con un laberinto generado de forma recursiva. Lo wque he ido completando son dos métodos en "FindPathAStar.cs".

"Search" ejecuta una iteración del algoritmo:

1. Comprueba si el nodo actual es la meta.
2. Recorre sus 4 vecinos y descarta los muros, los que quedan fuera del laberinto y los que ya están en CLOSED.
3. Calcula g, h y f de cada vecino válido, y lo añade a OPEN o lo actualiza si ya estaba.
4. Elige de OPEN el nodo con menor f, lo mueve a CLOSED y pasa a ser el nodo actual.

"GetPath" reconstruye el camino óptimo: parte del nodo final y sigue el "parent" de cada nodo hasta llegar al inicio.

[Captura 1: inicio y meta]
<img width="898" height="931" alt="image" src="https://github.com/user-attachments/assets/6327e914-7af0-4a3e-a030-462d04961776" />

[Captura 2: búsqueda en curso]
<img width="911" height="969" alt="image" src="https://github.com/user-attachments/assets/b8caeff0-b121-43e0-b2e3-d87a11fae10e" />

[Captura 3: camino óptimo]
<img width="921" height="936" alt="image" src="https://github.com/user-attachments/assets/c1d65086-5be9-418c-abd0-c7cf1301c373" />

Se aprecia cómo la búsqueda se dirige hacia la meta y deja zonas del laberinto sin explorar, que es justo la ventaja de la heurística frente a BFS.

## Conclusiones

- A* combina lo que ya se ha recorrido (g) con una estimación de lo que falta (h), lo que lo hace mucho más eficiente que BFS o DFS cuando se conoce la meta.
- La calidad de la heurística determina cuánto se explora. Con una heurística peor, A* explora más.
- Ver las listas OPEN y CLOSED en pantalla ayuda mucho a entender por qué el algoritmo elige cada nodo.

Repositorio: [https://github.com/Anpije/A-Search.git]
