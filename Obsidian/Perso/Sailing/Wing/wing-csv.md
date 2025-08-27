```dataviewjs
const pages = dv.pages('"Perso/Sailing/Wing"')
    .where(p => p.tags && p.tags.includes("wing"))
    .sort(p => p.Manufacturer);

let csv = [
  ["Name", "Manufacturer", "Model", "Available surface (m2)", "Pressure", "Span", "Surface", "Handles", "Material-core", "Material-spi", "Price", "Version", "Weight"]
];

for (let p of pages) {
  csv.push([
    p.Name ?? "",
    p.Manufacturer ?? "",
    p.Model ?? "",
    p["Available-surface"] ?? "",
    p.Pressure ?? "",
    p.Span ?? "",
    p.Surface ?? "",
    p.Handles ?? "",
    p["Material-core"] ?? "",
    p["Material-spi"] ?? "",
    p.Price ?? "",
    p.Version ?? "",
    p.Weight ?? ""
  ]);
}

// Format as CSV
// Use semicolon as separator for EU Excel
// Format as plain semicolon-separated CSV (EU-friendly)

let csvString = csv
  .map(row => row.map(field =>
    `"${String(field).replace(/"/g, '""')}"`
  ).join(";"))
  .join("\n");

// Show as plain paragraph, no code block
dv.el("pre", csvString);


