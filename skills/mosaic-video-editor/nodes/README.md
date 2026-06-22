# Node Reference

Each file below describes one node type (tile) available in Mosaic agents. Files contain the node type ID and a link to full parameter docs.

These files are orientation only. For accurate parameter names, accepted values, defaults, and examples, use the live docs or API response.

To discover nodes at runtime, call:

```
GET /node_types              — list all available node types
GET /node_type/{node_type_id} — get full parameter schema for a node
```

When building `update_params` for a run, use the `agent_node_id` from `GET /agent/{agent_id}` (not the node type ID). The node type ID tells you *what kind* of node it is; the agent node ID tells you *which instance* in a specific agent graph.

If a node file conflicts with `GET /node_type/{node_type_id}` or the corresponding page on [docs.mosaic.so](https://docs.mosaic.so), trust the live docs/API response.
