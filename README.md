# langgraph-codeact-excel-worker

This Agent helps you analyze Excel files with SQL and generate high-quality visualizations — powered by LangChain's new CodeAct agent type!

If you have any questions or would like to collaborate, feel free to reach out to me on [LinkedIn](https://www.linkedin.com/in/jenya-stoeva-60477249/). You're more than welcome!

## What is CodeAct

LangChain's CodeAct agents combine LLM reasoning with code execution, enabling dynamic problem solving through Python code. Rather than just calling predefined tools, CodeAct agents can generate, execute, and revise code on-the-fly using the tools you give them. This means your agent becomes:

* More flexible (able to work around missing tools)
* Safer (code runs in a local sandbox)
* Smarter (can generate multi-step logic, validate outputs, and even create visualizations dynamically)

## How It Works

This CodeAct agent helps you analyze Excel files using tools:

* **preview_excel_structure**: First, it inspects the file to understand the column names and data types.
* **complex_duckdb_query**: Then, it translates your question into SQL, runs the query via DuckDB, and preprocesses results for analysis.
* **create_visualization**: If a visualization is requested (or helpful), it builds one automatically using Plotly.

**❗ You can also bypass the built-in query and visualization tools by instructing the agent to ignore them. This will trigger its CodeAct capabilities to generate visualizations on its own!** 

The agent is instructed to:
* Clean data on ingest (whitespace, empty strings, various NaN values)
* Always validate SQL syntax
* Avoid using NULL or negative values by default
* Explain and format visualizations properly

## How-To

To run the agent, find the ```stream_from_agent()``` or ```run_agent()``` function at the end of the notebook. Configure the following:

* ```file_name```: The path to your Excel file (single-sheet only for now)
* ```user_query```: Your question (can include instructions like "ignore tools" or "visualize this")
* ```config```: Default recursion/thread options (already set to safe defaults)

## Key Capabilities

* Upload .xlsx files with any tabular data
* Ask SQL-like questions in plain English
* Get structured outputs or interactive visualizations (bar, line, pie, heatmap, Sankey, etc.)
* Automatically handles missing data, formatting issues, type mismatches
* **Works even if you ask it to ignore its tools and generate visualizations freely**

## Technical Highlights

* Agent Type: LangChain CodeAct
* LLM: OpenAI gpt-4o
* Execution: Local Python sandbox with eval() and stdout capture
* Data Engine: DuckDB for SQL queries
* Visualization: Plotly Express / Graph Objects
* Input: JSON-formatted strings for structured tool calls
* Output: Human-readable messages + JSON results





