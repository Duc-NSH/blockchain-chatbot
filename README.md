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

### Tool 1: introduce_myself
- **Description**: Gets information about the assistant and capabilities of assistant.
- **Inputs**: None

### Tool 2: search_internet
- **Description**: Retrieve all other information from internet when other tools are not suitable
- **Inputs**:
   - `search_query` (string): A complete and clear query to search google, without ambiguity.;

### Tool 3: get_token_price
- **Description**: Retrieve the prices of tokens on one or multiple chains.
- **Inputs**:
  - `list_token_symbol` (list[str]): List of symbols of all tokens to get the price of. For each token, please use all provided symbols in its data.
  - `list_chain_id` (list[str]): List of all chain IDs. Only include this input field if a specific chain to get token price on is provided.

### Tool 4: get_profile_wallet
- **Description**: Get detailed wallet information by address and blockchain network, including user wallet details.
- **Inputs**:
  - `wallet_address` (string): The address of the wallet.
  - `chain_name` (string): The name of the blockchain network to get the wallet profile from.
  - `chain_id` (string): The ID of the blockchain network to get the wallet profile from.

### Tool 5: get_ranking_token
- **Description**: Search for top and potential cryptocurrency tokens and provide investment advice based on token rankings, such as market cap, trading volume, trading volume change rate, etc.
- **Inputs**:
  - `orderBy` (string): Criteria for ranking tokens. The default is `tokenHealth`.

### Tool 6: retrieve_top_news
- **Description**: Retrieve the top news in the blockchain domain for the past 24 hours.
- **Inputs**: None

### Tool 7: get_defi_list
- **Description**: Retrieve the ranking list of DeFi applications such as lending pools, DEXes, yield farms, or searches for top DeFi applications based on Total Value Locked (TVL), TVL change rate, total users, total assets, or total assets change rate.
- **Inputs**:
  - `application_type` (string): The type of DeFi application.

### Tool 8: get_lending_assets
- **Description**: Retrieve the current borrow rates, deposit rates, borrow APY, and deposit APY of tokens on lending pools.
- **Inputs**:
  - `lending_pool_id` (list[str]): List of IDs of all lending pools.
  - `token_symbol` (list[str]): Token symbols to find the borrow and deposit rates.
  - `chain_id` (list[str]): List of chain IDs. Only include this input field if a specific chain is provided in the query.

### Tool 9: get_lending_information
- **Description**: Retrieve TVL (Total Value Locked), TVL change rate, number of users, real users ratio, total supply, total borrow, number of lenders, and number of borrowers in a specific lending pool.
- **Inputs**:
  - `list_lending_pool_id` (list[str]): List of IDs of all lending pools to retrieve information from.

### Tool 10: deposit_in_lendingpool
- **Description**: Execute token deposit transactions in a lending pool.
- **Inputs**:
  - `token_symbol` (string): The symbol of the token for the transaction.
  - `lending_pool_id` (string): The ID of the lending pool, extracted from entities.
  - `amount` (float): The amount to deposit. Use default if not provided.
  - `chain_id` (string): The ID of the chain for the transaction. Only include this field if a specific chain is provided.

### Tool 11: borrow_in_lendingpool
- **Description**: Execute token borrowing transactions in a lending pool.
- **Inputs**:
  - `token_symbol` (string): The symbol of the token for the transaction.
  - `lending_pool_id` (string): The ID of the lending pool, extracted from entities.
  - `amount` (float): The amount to borrow. Use default if not provided.
  - `chain_id` (string): The ID of the chain for the transaction. Only include this field if a specific chain is provided.

### Tool 12: withdraw_in_lendingpool
- **Description**: Execute token withdrawal transactions from a lending pool on chain.
- **Inputs**:
  - `token_symbol` (string): The symbol of the token for the transaction.
  - `lending_pool_id` (string): The ID of the lending pool, extracted from entities.
  - `amount` (float): The amount to withdraw. Use default if not provided.
  - `chain_id` (string): The ID of the chain for the transaction. Only include this field if a specific chain is provided.

### Tool 13: Repay_in_Lendingpool
- **Description**: Execute token repayment transactions in a lending pool.
- **Inputs**:
  - `token_symbol` (string): The symbol of the token for the transaction.
  - `lending_pool_id` (string): The ID of the lending pool, extracted from entities.
  - `amount` (float): The amount to repay. Use default if not provided.
  - `chain_id` (string): The ID of the chain for the transaction. Only include this field if a specific chain is provided.

### Tool 14: Transfer_in_Lendingpool
- **Description**: Transfer tokens from a lending pool.
- **Inputs**:
  - `token_symbol` (string): The symbol of the token for the transaction.
  - `lending_pool_id` (string): The ID of the lending pool, extracted from entities.
  - `amount` (float): The amount to transfer. Use default if not provided.
  - `chain_id` (string): The ID of the chain for the transaction. Only include this field if a specific chain is provided.

### Tool 15: Claim_Reward_in_Lendingpool
- **Description**: Claim rewards from a DeFi lending pool.
- **Inputs**:
  - `token_symbol` (string): The symbol of the token for the transaction.
  - `lending_pool_id` (string): The ID of the lending pool, extracted from entities.
  - `amount` (float): The amount of the reward to claim. Use default if not provided.
  - `chain_id` (string): The ID of the chain for the transaction. Only include this field if a specific chain is provided.

### Tool 16: convert_reward_in_Lendingpool
- **Description**: Convert reward tokens from a lending pool into other assets.
- **Inputs**:
  - `token_symbol` (string): The symbol of the token for the transaction.
  - `lending_pool_id` (string): The ID of the lending pool, extracted from entities.
  - `amount` (float): The amount to convert. Use default if not provided.
  - `chain_id` (string): The ID of the chain for the transaction. Only include this field if a specific chain is provided.

### Tool 17: staking_transaction
- **Description**: Execute staking transactions for assets.
- **Inputs**:
  - `asset_entity` (string): The cryptocurrency or vault entity to stake.
  - `amount` (float): The amount to stake.

### Tool 18: withdraw_from_staking
- **Description**: Withdraw staked assets or tokens from a staking pool.
- **Inputs**:
  - `asset_
  - entity` (string): The cryptocurrency or vault entity to withdraw.
  - `amount` (float): The amount to withdraw.

### Tool 19: claim_Rewards_from_staking
- **Description**: Claim rewards from assets staking activities.
- **Inputs**:
  - `asset_entity` (string): The cryptocurrency or vault entity to claim rewards from.
  - `amount` (float): The amount to claim.

### Tool 20: transfer_staked_token
- **Description**: Transfer staked tokens.
- **Inputs**:
  - `asset_entity` (string): The cryptocurrency or vault entity to transfer.
  - `amount` (float): The amount to transfer.

### Tool 21: lock_creation
- **Description**: Create a lock on assets or tokens for a specified period in governance.
- **Inputs**:
  - `asset_entity` (string): The cryptocurrency or vault entity to lock.
  - `amount` (float): The amount to lock.
  - `duration` (int): The duration in days for which to lock the assets in governance.

### Tool 22: lock_amount_increase
- **Description**: Increase the quantity of locked assets in a governance protocol.
- **Inputs**:
  - `asset_entity` (string): The cryptocurrency or vault entity to increase the lock for.
  - `amount` (float): The amount to increase the lock by.
  - `lock_id_entity` (int): The ID of the lock.

### Tool 23: unlock_duration_increase
- **Description**: Extend the lock duration of assets or tokens in governance.
- **Inputs**:
  - `asset_entity` (string): The cryptocurrency or vault entity for which to extend the lock duration.
  - `lock_id_entity` (int): The ID of the lock.
  - `duration` (int): The additional duration (in days) to extend the lock.

### Tool 24: withdraw_governance
- **Description**: Withdraw assets from governance by vault, token, or lock ID.
- **Inputs**:
  - `asset_entity` (string): The cryptocurrency or vault entity to withdraw.
  - `amount` (float): The amount to withdraw.

### Tool 25: merge_lock
- **Description**: Merge multiple locked asset positions into a single lock.
- **Inputs**:
  - `object_entity` (string): The governance object.
  - `transaction_type` (string): The type of transaction, in this case, "Merge".
  - `lock_id_1` (int): The first lock ID.
  - `lock_id_2` (int): The second lock ID.

### Tool 26: Compound_in_governance
- **Description**: Execute compound transactions within a governance protocol.
- **Inputs**:
  - `asset_entity` (string): The cryptocurrency or vault entity to compound.
  - `lock_id_entity` (int): The lock ID.
  - `amount` (float): The amount to compound.

