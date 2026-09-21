# ARCNM

**Know what any part should cost — and why.**

Manufacturing cost estimation from CAD and drawings. Send a STEP file and a
drawing; get back the process, the machines, the cycle times and the unit cost
at every lot size — each figure traced to the physics that produced it.

No black box. No guess weighted by a fudge factor. A cost you can defend in
front of the supplier who quoted you twice that.

---

### Built for code and for agents

```bash
curl -X POST https://api.arcnm.io/api/v1/calculations/upload-and-quote \
  -H "X-API-Key: $ARCNM_API_KEY" \
  -F "costing_environment_id=$ARCNM_ENV_ID" \
  -F "part_number=BRACKET-001" \
  -F "cad_file=@./bracket.step;type=application/step" \
  -F "drawing_file=@./bracket.pdf;type=application/pdf" \
  -F "lot_size=50"
```

Everything the dashboard does, the API does. **142 endpoints**, a public
OpenAPI spec, and an MCP server so Claude, Cursor or your own agent can quote a
part, rank its cost drivers and read the process plan as typed tools.

```json
{ "mcpServers": { "arcnm": { "url": "https://api.arcnm.io/mcp-server/mcp" } } }
```

Listed in the [MCP Registry](https://registry.modelcontextprotocol.io) as
`io.arcnm/arcnm`.

---

### Start here

| | |
|---|---|
| **[Quickstart](https://arcnm.io/docs/quickstart)** | First quote in five minutes — cURL, Python, TypeScript |
| **[API reference](https://arcnm.io/docs/api)** | Generated from the live OpenAPI spec, so it never drifts |
| **[MCP](https://arcnm.io/docs/mcp)** | Connect an agent or IDE over HTTP |
| **[Recipes](https://arcnm.io/docs/recipes/quote-a-part)** | Bulk RFQ triage, ERP sync, teaching the engine your actuals |
| **[Concepts](https://arcnm.io/docs/concepts/extraction)** | How extraction, cost modelling and calibration actually work |

Machine-readable index for agents: [`llms.txt`](https://arcnm.io/llms.txt) ·
[`llms-full.txt`](https://arcnm.io/llms-full.txt) ·
[API catalog](https://arcnm.io/.well-known/api-catalog)

---

### What it does

- **Reads the part.** Geometry, PMI and GD&T out of STEP files and PDF
  drawings, as a typed, ID-stable feature graph.
- **Plans the work.** 54 operation types across 26 machine classes, from CNC
  milling to metal printing, with treatments read off the drawing.
- **Prices every lot size.** Setup amortises, fixtures amortise once, tooling
  has a finite life, learning compounds — so a quote is a curve, not a number.
- **Learns your shop.** One batch of your own historical costs calibrates the
  engine to your machines, your rates and your reality.

---

<sub>Built by [rattle mng GmbH](https://arcnm.io/legal-notice) in Überlingen,
Germany · EU-hosted · [arcnm.io](https://arcnm.io) ·
[hello@arcnm.io](mailto:hello@arcnm.io)</sub>
