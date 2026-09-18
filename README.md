# Arbetsförmedlingen MCP Server

[![Listed in sweden-mcp-servers](https://img.shields.io/badge/listed%20in-sweden--mcp--servers-006aa7)](https://github.com/bsab/sweden-mcp-servers)

MCP server for the Swedish labour market. Built on [Arbetsförmedlingen](https://arbetsformedlingen.se) and [JobTech Dev](https://data.arbetsformedlingen.se/) open APIs.

Gives Claude and other MCP-compatible AI assistants 13 tools for searching jobs, streaming real-time events, AI-analysing job ads, and navigating the Swedish occupation taxonomy.

No API key required. All APIs are publicly accessible.

---

## Quick start

Requires Node.js 18 or later (`npx` is included with Node). No API key required.

Add to your Claude Desktop config (`%APPDATA%\Claude\claude_desktop_config.json` on Windows, `~/Library/Application Support/Claude/claude_desktop_config.json` on macOS):

```json
{
  "mcpServers": {
    "arbetsformedlingen": {
      "command": "npx",
      "args": ["-y", "arbetsformedlingen-mcp-server"]
    }
  }
}
```

Restart Claude Desktop. The 13 tools are now available.

---

## Tools

### JobSearch API
| Tool | What it does |
|------|-------------|
| `af_search_jobs` | Search live job listings by text, occupation, location, employer, employment type, etc. |
| `af_get_job` | Fetch a complete job listing by ID |
| `af_autocomplete` | Typeahead suggestions for search terms |

### JobStream API (real-time)
| Tool | What it does |
|------|-------------|
| `af_stream_jobs` | All new, updated and removed listings since a given datetime. Filter by occupation or location. |

### Historical Job Ads API
| Tool | What it does |
|------|-------------|
| `af_search_historical_jobs` | Search archived listings going back to 2006 |

### JobAd Enrichments API
| Tool | What it does |
|------|-------------|
| `af_enrich_job_text` | AI extracts occupations, competencies, traits and locations from a job ad text |
| `af_synonym_dictionary` | Synonym dictionary used for matching terms in job ads |

### JobAd Links API
| Tool | What it does |
|------|-------------|
| `af_search_job_links` | Search listings from the full Swedish market, including private job boards |

### JobEd Connect API
| Tool | What it does |
|------|-------------|
| `af_education_to_occupations` | Which occupations does a given education lead to? |
| `af_occupation_to_educations` | Which educations match an occupation's competency demands? |

### Taxonomy API
| Tool | What it does |
|------|-------------|
| `af_search_taxonomy` | Search occupations, skills, municipalities, regions. Returns concept IDs for filtering. |
| `af_get_taxonomy_concept` | Details about a taxonomy concept including parent/child relationships |
| `af_list_taxonomy_types` | List all concepts of a given type (e.g. all occupation fields or all regions) |

---

## Example prompts for Claude

```
Search for Python developer jobs in Stockholm
```
```
What are the top skills demanded in nurse job ads right now?
```
```
Which educations best match a career as a system developer?
```
```
Give me all job events from the last hour
```
```
Search the occupation taxonomy for "sjuksköterska" and show me the concept ID
```

---

## Other installation options

```bash
# Run directly (no install)
npx arbetsformedlingen-mcp-server

# Install globally
npm install -g arbetsformedlingen-mcp-server
arbetsformedlingen-mcp-server

# HTTP mode (for hosted AI agents)
TRANSPORT=http npx arbetsformedlingen-mcp-server
# listens on http://localhost:3000/mcp
# health check at http://localhost:3000/health
```

---

## Environment variables

| Variable | Default | Description |
|----------|---------|-------------|
| `TRANSPORT` | `stdio` | Set to `http` for HTTP/Streamable HTTP mode |
| `PORT` | `3000` | Port for HTTP mode |

---

## API documentation

- [JobSearch API](https://jobsearch.api.jobtechdev.se/)
- [JobStream API](https://jobstream.api.jobtechdev.se/)
- [Historical Job Ads API](https://historical.api.jobtechdev.se/)
- [JobAd Enrichments API](https://jobad-enrichments-api.jobtechdev.se/)
- [JobAd Links API](https://links.api.jobtechdev.se/)
- [JobEd Connect API](https://jobed-connect-api.jobtechdev.se/)
- [Taxonomy API](https://taxonomy.api.jobtechdev.se/)

---

## License

MIT
