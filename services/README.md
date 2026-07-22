# services.zkas.info

Static ZKAS ecosystem directory. It intentionally has no API dependency, so
users can still find the wallet, explorer, pool, node software, and recovery
resources during an individual service outage.

## Deploy

Serve this directory as the document root for `services.zkas.info`:

```text
root /var/www/services.zkas.info/html;
index index.html;
```

Copy `index.html` into that document root and configure HTTPS after the DNS A/AAAA
record resolves to the web server. No build step is required.

## Update listings

Each service is one `<article class="card">`. Keep these fields current:

- `data-category` controls task filters;
- `data-search` adds search synonyms;
- status text (`Live`, `Testing`, or `Developer preview`);
- trust/privacy badges;
- destination link.

Do not label a service `Live` solely because its landing page responds. Test its
primary user flow first.
