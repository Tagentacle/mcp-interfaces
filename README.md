# MCP Interfaces

> **The ROS of AI Agents** — MCP-related message schema definitions for the Tagentacle bus.

This is a Tagentacle **interface package** (`type = "interface"`) that defines the JSON Schema contracts for MCP-related Topics.

## Message Definitions

### MCPServerDescription (`/mcp/directory`)

Describes an MCP Server instance. Published by:
- **MCP Server Nodes** (`MCPServerNode` subclasses) on activation/deactivation
- **MCP Gateway Node** for stdio-adapted and remote servers

Consumed by:
- **Agent Nodes** for auto-discovery of available MCP servers
- **Dashboard / visualization** for topology overview

| Field | Type | Required | Description |
|-------|------|----------|-------------|
| `server_id` | string | yes | Unique identifier |
| `url` | string (URI) | yes | Streamable HTTP endpoint URL |
| `transport` | `"streamable-http"` | yes | Transport protocol |
| `concurrent_sessions` | boolean | no | Supports concurrent sessions (default: true) |
| `status` | `"available"` \| `"unavailable"` | yes | Current status |
| `source` | `"gateway"` \| `"node"` | yes | Publisher type |
| `tools_summary` | string[] | no | Tool name list for quick preview |
| `description` | string | no | Human-readable description |
| `publisher_node_id` | string | no | Node ID of the publisher |

## Usage

This package has **no Python dependencies**. It provides schema files for documentation, validation, and code generation.

Reference the schema in `tagentacle.toml`:
```toml
[topics."/mcp/directory"]
schema = "mcp_interfaces/msg/MCPServerDescription.json"
```

## License

MIT
