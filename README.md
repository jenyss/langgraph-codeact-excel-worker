# langgraph-codeact-excel-worker

This repository showcases examples of how to preview, query, and visualize data from Excel files — all powered by LangChain’s new CodeAct agent type!

**Check the Agent execution output in the Notebook to enjoy how it works!**

If you have any questions or would like to collaborate, feel free to reach out to me on [LinkedIn](https://www.linkedin.com/in/jenya-stoeva-60477249/). You're more than welcome!

## What is CodeAct

LangChain's CodeAct agents combine LLM reasoning with code execution, enabling dynamic problem solving through Python code. Rather than just calling predefined tools, CodeAct agents can generate, execute, and revise code on-the-fly using the tools you give them. This means your agent becomes:

* More flexible (able to work around missing tools)
* Safer (code runs in a local sandbox)
* Smarter (can generate multi-step logic, validate outputs, and even create visualizations dynamically)


## How It Works

### ```preview-tool-visualize-codeact```

This CodeAct agent allows you to explore and visualize Excel data by combining structural preview, SQL querying, and automatic chart generation, following a controlled execution flow enforced by a custom system prompt.

It supports the following workflow:

* Preview the file using ```preview_excel_structure``` to inspect column names, data types, and sample values.
* Translate user questions into DuckDB SQL queries based on the detected columns.
* Generate a visualization using Plotly, with support for user-specified chart types like bar, line, or Sankey.
* Display the result and finish the task only when all steps succeed.


### ```langgraph-codeact-excel-worker```

**NEEDS FIXING**
This CodeAct agent helps you analyze Excel files using tools:

* ```preview_excel_structure``` First, it inspects the file to understand the column names and data types.
* ```complex_duckdb_query``` Then, it translates your question into SQL, runs the query via DuckDB, and preprocesses results for analysis.
* ```create_visualization``` If a visualization is requested (or helpful), it builds one automatically using Plotly.


## How-To

To run the agent, find the ```stream_from_agent()``` or ```run_agent()``` function at the end of the notebook. Configure the following:

* ```file_name```: The path to your Excel file (single-sheet only for now)
* ```user_query```: Your question (can include instructions like "ignore tools" or "visualize this")
* ```config```: Default recursion/thread options (already set to safe defaults)
  

## Technical Highlights

* Agent Type: LangChain CodeAct
* LLM: OpenAI gpt-4o
* Execution: Local Python sandbox with eval() and stdout capture
* Data Engine: DuckDB for SQL queries
* Visualization: Plotly Express / Graph Objects





