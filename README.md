# Agentic RAG Chatbot with Tools-Learning Integration

## Introduction

The rapid evolution of artificial intelligence (AI) has led to the proliferation of conversational agents, commonly known as chatbots, that leverage Large Language Models (LLMs) to interact with users in natural language. Traditionally, these chatbots are limited to answering questions based solely on the knowledge encapsulated in their training data. While this capability is substantial, it presents a significant limitation: the inability to access real-time information or data beyond the training cut-off. This restriction hampers the practical utility of LLM-based chatbots in dynamic and data-intensive environments, such as blockchain technology, where real-time data is crucial.

In response to this limitation, our research introduces a novel chatbot system that extends the functionality of traditional LLM-based models by integrating real-time data retrieval through a suite of Application Programming Interfaces (APIs) within the blockchain domain. This development is particularly relevant as blockchain ecosystems are complex and continuously evolving, requiring users to access up-to-the-minute data for informed decision-making. Furthermore, the system is designed to handle both data-retrieval APIs and transaction-execution APIs, enabling a full range of interactions within the blockchain space.

The motivation behind this work stems from the growing demand for accessible tools that bridge the gap between technical complexity and user accessibility. Typically, interacting with APIs requires specialized knowledge and the ability to write code, which places such tools out of reach for non-developers. By embedding API integration within a chatbot, our system democratizes access to blockchain data, enabling end-users to query APIs using natural language without needing to understand the underlying technicalities. This approach enhances usability not only for blockchain technologies but also for any API-driven environment, offering users a seamless and flexible method to interact with real-time data and actions.

The proposed chatbot architecture addresses the challenges of integrating real-time APIs into a chatbot system with a variety of AI models. First, the LLM-based Query Refinement Agent enhances user queries to improve precision by refining vague or ambiguous requests. Next, the Entity Recognition Module uses the GLiNER model and Elastic Search to extract relevant entities from the user input, mapping them to API parameters. The API Filtering Module, powered by the LLM Embedder (a Bi-Encoder model) and BGE Rerank (a Cross-Encoder model), determines relevant APIs to apply to a given query, reducing unnecessary overhead and streamlining the execution process.

To achieve seamless communication between agents, we designed a multi-agent system consisting of Planning, Validation, Evaluation, and Response Generation Agents. This system functions like a team of experts, collaborating in an iterative loop to plan, validate, and generate the final response. The Planning Agent formulates the optimal strategy for handling multi-step queries, the Validation Agent removes hallucinations during planning, the Evaluation Agent checks the feasibility and correctness of the plan, and the Response Generation Agent compiles the final answer. 

We propose this novel architecture to bridge the gap between LLM-powered chatbots and API-driven interactions, ensuring accurate and efficient communication with real-time data sources. Our experimental results demonstrate the effectiveness of this system, achieving a 95% accuracy rate with low response times, making it highly suitable for dynamic environments like blockchain technology.

## Tool Descriptions

This repository documents the tools integrated within our chatbot system and their inputs. Below, you will find detailed descriptions of each tool, including its input parameters and operational capabilities.

### Tool 1: [Tool Name]
- **Description**: [Brief description of what this tool does]
- **Inputs**: [List of inputs required for this tool]

### Tool 2: [Tool Name]
- **Description**: [Brief description of what this tool does]
- **Inputs**: [List of inputs required for this tool]

### Tool 3: [Tool Name]
- **Description**: [Brief description of what this tool does]
- **Inputs**: [List of inputs required for this tool]
