```templater
<%*
const renderTable = await tp.user.renderTable;

const pages = dv.pages('"Perso/Sailing/Wing"')
    .where(p => p.tags && p.tags.includes("wing"));

// Column configuration
const columns = [
  { key: "file", label: "🗂️ File", get: p => `[${p.file.name}](${p.file.path})` },
  { key: "Name", label: "Name", get: p => p.Name ?? "" },
  { key: "Manufacturer", label: "Manufacturer", get: p => p.Manufacturer ?? "" },
  { key: "Model", label: "Model", get: p => p.Model ?? "" },
  { key: "Available-surface", label: "Avail. Surface (m²)", get: p =>
    Array.isArray(p["Available-surface"]) ? p["Available-surface"].join(", ") : (p["Available-surface"] ?? "")
  },
  { key: "Pressure", label: "Pressure (PSI)", get: p => p.Pressure ?? "" },
  { key: "Span", label: "Span (m)", get: p => p.Span ?? "" },
  { key: "Surface", label: "Surface (m²)", get: p => p.Surface ?? "" },
  { key: "Handles", label: "Handles", get: p =>
    Array.isArray(p.Handles) ? p.Handles.join(", ") : (p.Handles ?? "")
  },
  { key: "Material-core", label: "Core Material", get: p => p["Material-core"] ?? "" },
  { key: "Material-spi", label: "Canopy Material", get: p => p["Material-spi"] ?? "" },
  { key: "Price", label: "💰 Price (€)", get: p => p.Price !== undefined ? `${p.Price} €` : "" },
  { key: "Version", label: "Version", get: p => p.Version ?? "" },
  { key: "Weight", label: "⚖️ Weight (kg)", get: p => p.Weight !== undefined ? `${p.Weight} kg` : "" },
];

// Initial sort
let sortKey = "Span";
let ascending = true;

renderTable(pages, columns, dv.container);
// Render the table
const table = await renderTable(pages, columns); 
// Insert the table into the note 
await tp.file.append(table);
%>
```

