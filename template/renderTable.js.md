```js
async function renderTable(pages, columns, container) {
  let sortKey = "Span";
  let ascending = true;
  const sortedPages = pages.sort((a, b) => {
    const valA = a[sortKey] ?? "";
    const valB = b[sortKey] ?? "";
    if (valA < valB) return ascending ? -1 : 1;
    if (valA > valB) return ascending ? 1 : -1;
    return 0;
  });

  // Clear previous table
  container.innerHTML = "";

  // Export button
  const exportBtn = document.createElement("button");
  exportBtn.textContent = "📤 Export CSV";
  exportBtn.style.marginBottom = "8px";
  exportBtn.onclick = () => {
    const csv = [
      columns.map(col => `"${col.label}"`).join(";"),
      ...sortedPages.map(p =>
        columns.map(col =>
          `"${String(col.get(p)).replace(/"/g, '""')}"`
        ).join(";")
      )
    ].join("\n");

    const blob = new Blob([csv], { type: "text/csv;charset=utf-8;" });
    const link = document.createElement("a");
    link.href = URL.createObjectURL(blob);
    link.download = "wings.csv";
    link.click();
  };
  container.appendChild(exportBtn);

  // Create table
  const table = document.createElement("table");
  table.style.borderCollapse = "collapse";
  table.style.width = "100%";
  table.style.fontSize = "0.9em";

  // Header
  const thead = document.createElement("thead");
  const headerRow = document.createElement("tr");
  headerRow.style.position = "sticky";
  headerRow.style.top = "0";
  headerRow.style.background = "#777777";
  headerRow.style.zIndex = "1";

  columns.forEach(col => {
    const th = document.createElement("th");
    th.innerText = col.label;
    th.style.padding = "6px";
    th.style.borderBottom = "2px solid #ccc";
    th.style.borderRight = "1px solid #eee";
    th.style.textAlign = "left";
    th.style.cursor = "pointer";
    th.onclick = () => {
      if (sortKey === col.key) {
        ascending = !ascending;
      } else {
        sortKey = col.key;
        ascending = true;
      }
      renderTable(pages);
    };
    headerRow.appendChild(th);
  });
  thead.appendChild(headerRow);
  table.appendChild(thead);

  // Body
  const tbody = document.createElement("tbody");
  sortedPages.forEach((p, index) => {
    const row = document.createElement("tr");
    if (index % 2 === 1) row.style.backgroundColor = "#555555";

    columns.forEach((col, i) => {
      const td = document.createElement("td");
      td.style.padding = "6px";
      td.style.borderRight = "1px solid #eee";

      const val = col.get(p);
      if (i === 0 && val.includes("](")) {
        // render Markdown link as HTML
        const match = val.match(/\[(.*?)\]\((.*?)\)/);
        if (match) {
          const a = document.createElement("a");
          a.href = match[2];
          a.innerText = match[1];
          a.onclick = e => {
            e.preventDefault();
            app.workspace.openLinkText(match[2], "", false);
          };
          td.appendChild(a);
        } else {
          td.innerText = val;
        }
      } else {
        td.innerText = val;
      }

      row.appendChild(td);
    });

    tbody.appendChild(row);
  });
  table.appendChild(tbody);

  container.appendChild(table);
}

};
module.exports = renderTable;
```
