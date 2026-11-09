# ALLR Motorcycle Gear Prices (MCP server)

ALLR compares motorcycle gear prices (helmets, jackets, suits, pants, boots, gloves, protection, luggage) across 50+ retailers in Canada, the US, the EU and the UK, ranked by **landed cost**: item price + shipping + import duty + customs brokerage, in the buyer's currency.

This repository holds the public listing for ALLR's hosted MCP server: its [`server.json`](server.json) for the [official MCP Registry](https://registry.modelcontextprotocol.io) (`io.github.dfedarchuk/allr`) and connection details. The server itself is hosted by ALLR; there is nothing to install or run.

## Connect

| | |
|---|---|
| Endpoint | `https://allr.io/mcp` |
| Transport | Streamable HTTP (stateless JSON-RPC over POST) |
| Authentication | None. Public and read-only. |
| Rate limit | 300 requests per minute per IP |

Claude Code:

```sh
claude mcp add --transport http allr https://allr.io/mcp
```

Any other MCP client: add a remote (HTTP) server with the URL `https://allr.io/mcp` and no authentication.

## Tools

All five tools are read-only.

| Tool | What it does |
|---|---|
| `search_gear` | Search the catalog by free text; returns each product's lowest landed price for a buyer country and its allr.io page. |
| `get_product_offers` | Per-retailer landed-cost table for one product (price, shipping, duty, brokerage), cheapest first. |
| `get_deals` | Gear currently discounted, below MSRP or below the store's own advertised price. |
| `get_size_recommendation` | Recommends a size from body measurements against the manufacturer's size chart. |
| `list_categories_and_brands` | Valid category and brand values for the filters. |

Every price tool takes a `country` (`CA`, `US`, `EU`, `UK`). Destination sales tax / VAT is not included.

## More

- Full developer documentation: https://allr.io/developers
- Website: https://allr.io
- Support: support@allr.io
