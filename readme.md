# 🎬 Degrees of Separation: Actor Connection Finder

This project is based on the "Six Degrees of Kevin Bacon" concept, where any actor in the film industry can be connected to another through shared movie appearances. In this assignment, you will complete a **Breadth-First Search (BFS)** algorithm to find the shortest connection path between any two actors using real movie data.



## 📁 Dataset Overview

The project contains two sets of CSV data files:
- `large/` — Full IMDb-like dataset (slow for testing)
- `small/` — A smaller sample dataset (ideal for development)

Each directory contains:

| File Name       | Description |
|-----------------|-------------|
| `people.csv`    | Maps `person_id` to actor `name` and `birth year` |
| `movies.csv`    | Maps `movie_id` to `title` and `year` |
| `stars.csv`     | Maps which actors (`person_id`) starred in which movies (`movie_id`) |

### Example:
- A row in `stars.csv` might say: `person_id=102` and `movie_id=104257`
- Looking them up reveals: _Kevin Bacon_ starred in _A Few Good Men_


## 📄 Codebase Structure

- `degrees.py` — Main script
- `util.py` — Contains `Node`, `StackFrontier`, and `QueueFrontier` classes for search
- `people.csv`, `movies.csv`, `stars.csv` — Data files
- `small/` and `large/` — Data folders



## 🔍 How It Works

1. Data is loaded into memory using `load_data()`, which populates:
   - `names`: `{lowercase name → set of IDs}`
   - `people`: `{id → {"name", "birth", "movies"}}`
   - `movies`: `{id → {"title", "year", "stars"}}`

2. The user is prompted to enter two actor names.

3. Using `person_id_for_name`, their IMDb IDs are retrieved.

4. The function `shortest_path(source_id, target_id)` is then called.

---
---
---

## ✏️ Your Task

### Implement the following function in `degrees.py`:

```python
def shortest_path(source, target):
    """
    Returns the shortest list of (movie_id, person_id) pairs
    that connect the source to the target actor.
    """
```

## ✅ Specification
- Return a list of tuples: [(movie_id1, person_id1), (movie_id2, person_id2), ...]

- Each tuple means the person appeared in movie_id with person_id

- If multiple paths exist, any shortest one is acceptable

- If no path exists, return None

- Use the helper: neighbors_for_person(person_id) to get connections

## 🚫 Constraints

Do NOT:

- Modify any part of the code outside the shortest_path() function (unless creating helper functions)

- Import external libraries (only use standard Python modules)

🧪 Example Output
```console
Name: Jennifer Lawrence
Name: Tom Hanks

2 degrees of separation.
1: Jennifer Lawrence and Kevin Bacon starred in X-Men: First Class
2: Kevin Bacon and Tom Hanks starred in Apollo 13
```