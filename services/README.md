# services.zkas.info

Static ZKAS ecosystem directory. `services.v1.json` is the canonical,
machine-readable directory used by the ZKAS wallet. The wallet retains its last
valid copy and a bundled fallback, so this site being unavailable cannot blank
the wallet's Services page.

## Deploy

Serve this directory as the document root for `services.zkas.info`:

```text
root /var/www/services.zkas.info/html;
index index.html;
```

Copy `index.html` and `services.v1.json` into that document root and configure
HTTPS after the DNS A/AAAA record resolves to the web server. No build step is
required. Serve the JSON with `Access-Control-Allow-Origin: *`; the wallet does
not send credentials to this endpoint.

## Update listings

Update `services.v1.json` first. A valid change becomes visible in the wallet the
next time its Services page opens; no wallet release is required. Keep IDs
stable, increment `schema_version` only for an incompatible schema change, and
use HTTPS links only.

The static website currently keeps matching `<article class="card">` fallback
markup for resilience and search-engine rendering. Keep these fields aligned:

- `data-category` controls task filters;
- `data-search` adds search synonyms;
- status text (`Live`, `Testing`, or `Developer preview`);
- trust/privacy badges;
- destination link.

Do not label a service `Live` solely because its landing page responds. Test its
primary user flow first.
