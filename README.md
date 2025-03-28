# langgraph-codeact-excel-worker

# Excel Analysis Agent (LangChain CodeAct)

This project provides a LangChain **CodeAct agent** that enables robust, tool-driven Excel analysis using SQL (via DuckDB) and visualization (via Plotly). It’s designed to be **plug-and-play**, intuitive, and resilient for real-world Excel data.

---

## Tools

| Tool Name                | Description                                                                 |
|--------------------------|-----------------------------------------------------------------------------|
| `preview_excel_structure` | Previews columns, types, and sample data from an Excel file.                |
| `complex_duckdb_query`    | Executes SQL queries using DuckDB, optimized for Excel and null-safe logic. |
| `create_visualization`    | Converts query results into Plotly visualizations with smart layouting.     |

---

## How It Works

1. **Preprocessing**: Cleans Excel data (`null`, `NaN`, whitespace) to ensure reliable querying.
2. **Tool-first Planning**: The agent is prompted to always preview data, validate SQL logic, and decide whether to visualize.
3. **Visualization Automation**: If requested or useful, the agent will build a new chart (e.g. line, Sankey) using Plotly—without relying on a predefined tool.


