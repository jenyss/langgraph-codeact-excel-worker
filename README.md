# langgraph-codeact-excel-worker

This Agent helps you analyze Excel files with SQL and generate high-quality visualizations — powered by LangChain's new CodeAct agent type!

## What is CodeAct

LangChain's CodeAct agents combine LLM reasoning with code execution, enabling dynamic problem solving through Python code. Rather than just calling predefined tools, CodeAct agents can generate, execute, and revise code on-the-fly using the tools you give them. This means your agent becomes:

* More flexible (able to work around missing tools)
* Safer (code runs in a local sandbox)
* Smarter (can generate multi-step logic, validate outputs, and even create visualizations dynamically)

## How It Works

This CodeAct agent helps you analyze Excel files using:

* **preview_excel_structure**: First, it inspects the file to understand the column names and data types.

* **complex_duckdb_query**: Then, it translates your question into SQL, runs the query via DuckDB, and preprocesses results for analysis.

create_visualization: If a visualization is requested (or helpful), it builds one automatically using Plotly.

The agent is instructed to:

Clean data on ingest (whitespace, empty strings, various NaN values)

Always validate SQL syntax

Avoid using NULL or negative values by default

Explain and format visualizations properly


## Tools

| Tool Name                | Description                                                                 |
|--------------------------|-----------------------------------------------------------------------------|
| `preview_excel_structure` | Previews columns, types, and sample data from an Excel file.                |
| `complex_duckdb_query`    | Executes SQL queries using DuckDB, optimized for Excel and null-safe logic. |
| `create_visualization`    | Converts query results into Plotly visualizations with smart layouting.     |




