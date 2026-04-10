# Customization

## Change the target lead profile

Edit these fields in `⚙️ CONFIGURE HERE`:

### `SEARCH_GOAL`
A short sentence describing who you want to find.

Example:
`Find startup CTOs in Singapore who recently raised a Series A`

### `IDEAL_LEAD_DESCRIPTION`
A more detailed paragraph describing the ideal lead.

Example:
`Technical founders or CTOs at venture-backed startups in Singapore, ideally post-seed to Series A, likely hiring engineers or building AI products.`

### `SEARCH_QUERIES`
One Google query per line.

Examples:

```text
site:linkedin.com/in "CTO" startup Singapore "Series A"
site:linkedin.com/in founder OR "co-founder" fintech Singapore
site:linkedin.com/in "engineering manager" "open to work" Singapore
```

## Adjust scoring strictness

The threshold currently saves only profiles with score `>= 0.5`.

To change it, edit the `Parse + Filter Leads` code node.

## Adjust volume

The workflow currently uses 10 queries and 3 pages per query.

To change page depth, edit `Build Query + Page List` and update:

```js
const pages = [1, 11, 21];
```

## Change email format

Edit the `Format Email` node to:

- alter branding
- change top lead count
- simplify or expand the digest
