# Project Title: AI-Powered Data Discovery Agent.
# The Problem: 
Data Analysts often spend 40% of their time just finding which tables contain the data they need.
# The Solution: 
A Gemini-powered agent using the Model Context Protocol (MCP) to interact directly with database schemas via natural language.
# Tech Stack: 
* Orchestration: Google ADK (Agent Development Kit).
# Model: 
Gemini 1.5 Flash.
# Protocol: 
MCP (Model Context Protocol).
# Compute: 
Google Cloud Run (Serverless).

# On MCP (The Protocol): 
"I used MCP because it separates the AI's reasoning from the tool's execution. This is critical for data security—the LLM never sees the raw database credentials; it only interacts with the standardized MCP interface."

# On ADK (The Framework): 
"Google's Agent Development Kit allowed me to build a 'Sequential Agent.' This ensures the agent first inspects the schema before it attempts to write a SQL query, reducing hallucinations."

# On Cloud Run (The Deployment): 
"By deploying as a serverless container on Cloud Run, the system is highly scalable and cost-effective, only consuming resources when a query is actually being processed."

# The project works in a 3-step loop:

# User Input: 
"What was our highest selling product in Bengaluru last month?"
# Reasoning (Gemini): 
"I need to know the schema of the sales table first." -> Calls get_schema() tool.
# Action (MCP):  "
The tool returns the column names. Gemini then writes the SQL and calls run_query().
-------------------------------------------------------------------------------------------
# Data-Driven-AI-Architect-Agentic-Data-Discovery
An enterprise-grade AI Agent built using the Google Agent Development Kit (ADK) and Gemini 1.5 Flash. This project demonstrates how to bridge the gap between Large Language Models (LLMs) and structured data warehouses like BigQuery using the Model Context Protocol (MCP).

# Problem Statement
Data Analyst and Engineers often spend 30-40% of their time simply performing "Data Discovery"-
finding which tables exist, understanding schemas, and verifying column names before writing a single line of SQL.

# The Solution: This AI Agent acts as an intelligent interface that:
1.Explores available database and tables.
2.Inspects schemas to understand data types and relationships.
3.Executes validated SQL queries to provide immediate insights via natural language.

# Techincal Architecture
The Project follows a Decoupled Agentic Architecture. By using the Model Context Protocol (MCP), the LLM's reasoning is repeated is separated from the data execution layer,ensuring security and modularity
# Orchestration: 
Google ADK(Agent Development Kit)
# LLM : 
Gemini 1.5 Flash(via Vertex AI)
# Data Layer: 
Google Big Query (Public  Data sets or Custom Schemas0
# Protocol: 
MCP for tool-calling and data retrieval.

# System workflow
The agent follows a "Schema-First" reasoning loop to eliminate SQL syntax hallunications:
1. User Inquiry:" What were the top 5 trending products last  month?"
2. Discovery:  Agent calls list_tables() to identify the relevant table.
3. Validation : Agent calls get_table_schema() to confirm column names(e.g.,product_name vs item_id).
4. Execution: Agent generates and runs a precise SQL query via run_query().
5. Syntesis: Data is returned and sumarized in natural language.

# Security & Best Practices
 As a Data Engineer, I have implemented the following production standards:
 # Identify & Access Management(IAM): 
 The agent operates under a service account with "Least Privilege" (Big Query Data Viewer & Vertex AI User).

 # Environment Isolation: 
 Sensitive configurations are handled via Cloud Run environment  variables, never hardcoded.

 # Ready-Only Access:
 The MCP tools are strictly limited to SELECT statements to prevent accidental data modification.

 # Future Roadmap
[] Integrate Vector Search in AlloyDB for unstructured data retrieval.

[] Add Data Quality checks(Great Expectations) within the toolset.

[] Implement a frontend UI using Streamlit.










