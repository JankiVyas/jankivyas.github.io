# Browser CSV Chart Standard

Use this pattern to build static, browser-side charts from repository CSV data. Charts should read their source at runtime, aggregate the rows in JavaScript, and use restrained styling consistent with Studio Clarity.

## Dependencies

Load PapaParse and Chart.js from trusted CDN URLs in the HTML document. Pin explicit versions where practical. Do not introduce a build step or a server-side data pipeline for a static chart.

```html
<script src="https://cdn.jsdelivr.net/npm/papaparse@5.4.1/papaparse.min.js" defer></script>
<script src="https://cdn.jsdelivr.net/npm/chart.js@4.4.7/dist/chart.umd.min.js" defer></script>
```

Ensure chart initialization runs only after both libraries and the chart canvas are ready.

## Load CSV data

Fetch the data file using a path relative to the page. For a page in a `decks/` directory, repository data files are addressed through `../data/`:

```js
const response = await fetch('../data/retail-q4/retail_performance.csv');
if (!response.ok) throw new Error(`Could not load CSV (${response.status})`);
const csvText = await response.text();
const parsed = Papa.parse(csvText, { header: true, skipEmptyLines: true, dynamicTyping: true });
if (parsed.errors.length) console.warn('CSV parsing warnings:', parsed.errors);
const rows = parsed.data;
```

Handle fetch, parse, and empty-data errors with a clear message in the page; do not leave a blank chart with no explanation. Static hosting must serve the CSV as a sibling repository asset. For local testing, use a static web server because browser `fetch()` may be blocked for `file://` URLs.

## Aggregate in JavaScript

Compute chart metrics from the parsed rows rather than hard-coding chart values. Filter to the desired period, segment, region, or other dimension, then group and sum or average the numeric metric as appropriate. For example, to sum revenue by segment in Q3:

```js
const q3 = rows.filter(row => row.Quarter === 'Q3 2026');
const totals = q3.reduce((result, row) => {
  const key = row.Segment;
  result[key] = (result[key] || 0) + Number(row.Revenue_USD || 0);
  return result;
}, {});
const labels = Object.keys(totals);
const values = labels.map(label => totals[label]);
```

Use a weighted calculation when aggregating rates or percentages (for example, weight gross margin by revenue) rather than taking an unweighted mean of row-level percentages. Label units and aggregation period clearly.

## Chart styling

- Use Chart.js with responsive sizing and a legible aspect ratio.
- Remove visual clutter: hide heavy gridlines (use `grid.display: false` or very light lines), hide unnecessary legends, and minimize ticks and borders. Do not remove labels needed to understand the values.
- Highlight the top-performing bar in **terracotta `#B85D38`**; style comparison bars in **soft sand `#DCD5C9`**.
- Determine the winning value from the live aggregate, not a hard-coded category. Keep category labels and tooltips informative.
- Supply an accessible canvas name and a text fallback or nearby summary for chart meaning and data-load errors.

## Quality checklist

1. CSV is fetched from the correct `../data/` relative path.
2. PapaParse reads headers and Chart.js receives dynamically aggregated values.
3. Numeric fields are parsed safely; missing or invalid values do not silently distort totals.
4. The winning bar is calculated at runtime and highlighted in terracotta; all other comparison bars use soft sand.
5. Gridlines and legends are suppressed unless they add necessary context.
6. Loading failures and chart interpretation remain available to visitors without relying on hover alone.
