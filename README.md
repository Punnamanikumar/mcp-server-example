5-mcp-server-deepdive-deployment
=================================

Minimal Python MCP server (FastMCP) exposing a simple `add(a, b)` tool.

Installation
------------

Prerequisites:
- Python 3.12+

Set up a virtual environment and install the project:

```bash
python -m venv .venv
source .venv/bin/activate
pip install -e .
```

Optional: If you use `uv` for tooling, install via Homebrew:

```bash
brew install uv
```

You can later run the server during development with `mcp dev python -m mcpserver` or the console script `mcp dev mcp-server`.

Run (dev)
---------
Use one of the following:

```bash
mcp dev python -m mcpserver
# or
mcp dev mcp-server
```

Note: Avoid `mcp dev ./src/mcpserver/__main__.py` — `mcp dev` expects a command, not a file path.

Claude Desktop Config
---------------------
To run the server via `uvx` using a git repo (as in your setup), add an MCP server entry like `add_tool`:

```json
{
	"mcpServers": {
		"add_tool": {
			"command": "/Users/punnamanikumar/.local/bin/uvx",
			"args": [
				"--from",
				"git+https://github.com/Punnamanikumar/mcp-server-example.git",
				"python3",
				"-m",
				"mcpserver"
			],
			"env": {
				"PATH": "/Users/punnamanikumar/.local/bin:/opt/homebrew/bin:/usr/local/bin:/usr/bin:/bin:/usr/sbin:/sbin"
			}
		}
	}
}
```

Alternatively, to use your local workspace directly (no `uvx`):

```json
{
	"mcpServers": {
		"local-mcp": {
			"command": "python3",
			"args": ["-m", "mcpserver"]
		}
	}
}
```
