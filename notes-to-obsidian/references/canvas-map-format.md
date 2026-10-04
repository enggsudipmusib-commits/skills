# Canvas concept map format

Obsidian's `.canvas` files are JSON. This is the minimum structure needed for a readable topic map — don't add fields Obsidian doesn't use.

```json
{
  "nodes": [
    { "id": "n1", "type": "file", "file": "Topic 1 - <Name>.md", "x": 0,    "y": 0,   "width": 250, "height": 100 },
    { "id": "n2", "type": "file", "file": "Topic 2 - <Name>.md", "x": 300,  "y": 0,   "width": 250, "height": 100 },
    { "id": "g1", "type": "group", "label": "<Unit/Chapter name>", "x": -20, "y": -40, "width": 620, "height": 200 }
  ],
  "edges": [
    { "id": "e1", "fromNode": "n1", "toNode": "n2", "label": "prerequisite for" }
  ]
}
```

## Rules

- One `file` node per topic note, referencing the exact filename used in Step 5 (so clicking the node opens the real note in the vault).
- Lay nodes out left-to-right or top-to-bottom in the order the notes' own structure implies (prerequisite chains, chapter order) — don't scatter them randomly.
- Use `group` nodes to visually cluster topics that belong to the same unit/chapter when there are more than ~4 topics.
- Only draw an edge where the notes themselves establish a relationship: an explicit `[[wikilink]]` between the two topic notes, a stated prerequisite, or a stated "builds on" relationship. If you're unsure whether a connection is real, leave the edge out rather than guessing.
- Label edges when the relationship type matters ("prerequisite for", "contrasts with") — an unlabeled edge just means "related."
- Keep the layout readable: don't overlap nodes, leave at least 50px between adjacent nodes.
- Save the file as `<Unit/Chapter name> Map.canvas` in the same location as the topic notes it references.
