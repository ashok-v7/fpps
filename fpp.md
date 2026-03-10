Act as a Senior AI Engineer, AWS FinOps Architect, and Python developer.

Your task is to build a complete working Proof of Concept (POC) for an "AWS FinOps Autonomous Agent".

The solution must follow an agentic architecture where an AI agent can reason about AWS costs and use tools to gather data and provide optimization recommendations.

Important constraints:

* Do NOT use Amazon Bedrock models.
* The LLM must be Azure OpenAI GPT-4.1.
* The agent framework must be Strands Agents SDK.
* AWS APIs must be accessed using boto3.
* The solution must run locally.

The agent must support tool calling and should automatically decide which tool to invoke.

The tools required are:

1. AWS Cost Explorer

   * Retrieve cost grouped by service
   * Analyze last month cost

2. AWS Compute Optimizer

   * Retrieve EC2 rightsizing recommendations

3. AWS Trusted Advisor

   * Retrieve cost optimization checks

The AI agent should behave like a Senior AWS FinOps Engineer and must:

* analyze AWS spending
* detect high cost services
* identify optimization opportunities
* recommend cost reduction actions
* estimate savings where possible

Provide the following sections in your response.

SECTION 1 — Architecture

Provide a clear architecture explanation showing:

User
↓
FinOps Agent
↓
Azure OpenAI GPT-4.1
↓
AWS Tools
↓
AWS APIs

Explain how reasoning and tool calling works.

SECTION 2 — Project Folder Structure

Provide a complete Python project structure such as:

finops-agent
│
├── app.py
├── config.py
├── requirements.txt
│
├── llm
│   └── azure_openai_model.py
│
├── tools
│   ├── cost_explorer_tool.py
│   ├── compute_optimizer_tool.py
│   └── trusted_advisor_tool.py
│
└── prompts
└── system_prompt.txt

Explain the purpose of each file.

SECTION 3 — Requirements File

Generate a requirements.txt containing all dependencies required to run the application.

SECTION 4 — Azure OpenAI Integration

Create a Python module called:

llm/azure_openai_model.py

It must:

* integrate Azure OpenAI GPT-4.1
* expose an invoke(messages) method
* read configuration from environment variables
* support chat completions
* include error handling

SECTION 5 — AWS Tools Implementation

Create three tools compatible with Strands Agents SDK using the @tool decorator.

Tool 1:
get_aws_cost_last_month()

Uses AWS Cost Explorer to return cost grouped by service.

Tool 2:
get_ec2_rightsizing_recommendations()

Uses Compute Optimizer API to return EC2 rightsizing suggestions.

Tool 3:
get_trusted_advisor_cost_recommendations()

Uses Trusted Advisor API to retrieve cost optimization checks.

Each tool must:

* use boto3
* include docstrings
* return structured JSON
* include example output

SECTION 6 — FinOps Agent Prompt

Create a system prompt for the FinOps agent that instructs it to:

* always call tools to retrieve real AWS data
* analyze costs like a FinOps expert
* provide structured optimization recommendations
* estimate cost savings where possible

SECTION 7 — FinOps Agent Implementation

Create the main agent implementation in:

app.py

The implementation must:

* initialize AzureOpenAIModel
* register all AWS tools
* create a Strands Agent
* include a CLI interface where the user can ask questions
* display the agent response

Example CLI:

Ask FinOps Agent > Why is my AWS bill high?

SECTION 8 — Configuration

Create a config.py that loads environment variables:

AZURE_OPENAI_API_KEY
AZURE_OPENAI_ENDPOINT
AZURE_OPENAI_DEPLOYMENT
AZURE_OPENAI_API_VERSION

SECTION 9 — Environment Setup

Provide instructions for:

1. Installing dependencies
2. Setting AWS credentials
3. Setting Azure OpenAI environment variables
4. Running the agent

SECTION 10 — Example Queries

Provide example user prompts such as:

* Why is my AWS bill high?
* Which service costs the most?
* Show EC2 optimization opportunities.
* What are Trusted Advisor cost recommendations?

SECTION 11 — Example Agent Output

Provide example responses from the agent showing:

* cost breakdown
* optimization recommendations
* estimated savings.

The final result should be a complete working Python application that demonstrates an autonomous AWS FinOps agent using Azure OpenAI GPT-4.1 and Strands Agents SDK.

Ensure all code blocks are complete and runnable.
