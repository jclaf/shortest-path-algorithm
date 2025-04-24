# Shortest path algorithm

Recherche des plus courts chemins depuis un sommet de départ dans un graphe pondéré, en utilisant l’algorithme de Dijkstra.
Il affiche la distance minimale et le chemin correspondant pour chaque sommet.

## Description

### 1. Définition du graphe

```python
my_graph = {
    'A': [('B', 5), ('C', 3), ('E', 11)],
    'B': [('A', 5), ('C', 1), ('F', 2)],
    'C': [('A', 3), ('B', 1), ('D', 1), ('E', 5)],
    'D': [('C',1 ), ('E', 9), ('F', 3)],
    'E': [('A', 11), ('C', 5), ('D', 9)],
    'F': [('B', 2), ('D', 3)]
}
```
- **Structure** : C’est un dictionnaire Python représentant un graphe non orienté pondéré.
- **Clés** : Les noms des sommets ('A', 'B', etc.).
- **Valeurs** : Une liste de tuples `(voisin, poids)` indiquant les voisins et le coût pour les atteindre.

---

### 2. Fonction `shortest_path`

**But** : Trouver et afficher les plus courts chemins depuis un sommet de départ vers tous les autres sommets (ou un sommet cible spécifique).

#### Étapes principales :

1. **Initialisation**
   - `unvisited` : liste des sommets à visiter.
   - `distances` : dictionnaire des distances minimales connues depuis le départ (0 pour le départ, infini pour les autres).
   - `paths` : dictionnaire des chemins pour chaque sommet.
   - Le chemin de départ est initialisé avec le sommet de départ.

2. **Boucle principale**
   - Tant qu’il reste des sommets non visités :
     - On sélectionne le sommet non visité avec la plus petite distance connue (`current`).
     - Pour chaque voisin de `current`, on vérifie si le chemin passant par `current` est plus court que celui déjà trouvé :
        - Si oui, on met à jour la distance et le chemin.
        - On gère la construction du chemin pour éviter des doublons.
     - On marque `current` comme visité (on le retire de `unvisited`).

3. **Affichage des résultats**
   - Si `target` est précisé, on affiche uniquement ce sommet, sinon tous.
   - Pour chaque sommet atteint, on affiche la distance et le chemin.

4. **Retour**
   - La fonction retourne les dictionnaires `distances` et `paths`.

---

### 3. Exécution

```python
if __name__ == "__main__":
    shortest_path(my_graph, 'A')
```
- Lance la recherche des plus courts chemins depuis le sommet 'A'.

---

## Algorithme Utilisé

### Dijkstra

L’algorithme implémenté ici est **l’algorithme de Dijkstra**.  
#### **Principe :**
- C’est un algorithme classique pour trouver le plus court chemin entre un sommet de départ et tous les autres sommets dans un graphe pondéré (avec des poids positifs).
- À chaque étape, il choisit le sommet non visité avec la plus petite distance connue, puis met à jour les distances de ses voisins.
- Il garantit que, lorsqu’un sommet est marqué comme visité, la plus courte distance pour l’atteindre est trouvée.

#### **Limites de l’implémentation :**
- Cette version utilise une liste pour gérer les sommets non visités, ce qui la rend moins efficace que la version utilisant une file de priorité (heap).
- La gestion des chemins (`paths`) est un peu artisanale et pourrait être simplifiée.

---
