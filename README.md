# Conversational_database_agent_mongoDB



# Conversational MongoDB Database Agent 

## Table of Contents

- [Introduction](#introduction)
- [Features](#features)
- [Architecture Overview](#architecture-overview)
- [Dataset Used](#dataset-used)
- [Setup \& Implementation in Notebook](#setup--implementation-in-notebook)
- [Usage](#usage)



---

## Introduction

Conversational MongoDB Database Agent is an interactive chatbot that lets you ask questions about your MongoDB data in plain English. Powered by Google Gemini and MongoDB Atlas, it automatically translates your questions into database queries and responds conversationally, making data exploration easy for everyone—all from a Jupyter or Colab notebook.

---

## Features

- Conversational interface: Ask questions in natural language
- Automatic query translation: Converts English to MongoDB queries using Google Gemini
- Context awareness: Remembers previous questions for follow-up queries
- Flexible analytics: Supports searching, counting, aggregation, summation, and percentage calculations
- Web UI: Simple chat interface built with Gradio

---

## Architecture Overview

```
+-------------------+         +---------------------+         +----------------+
|   Gradio UI       | <-----> | Conversational Agent| <-----> |  MongoDB Atlas |
+-------------------+         +---------------------+         +----------------+
        |                               |                               |
        |         +---------------------+                               |
        |         |  - Handles chat flow                                |
        |         |  - Manages context/memory                           |
        |         |  - Orchestrates NLP, DB, and response modules       |
        |         +---------------------+                               |
        |                               |                               |
        |        +----------------------+                               |
        |        | NLPProcessor         |                               |
        |        | - Understands intent |                               |
        |        | - Translates English |                               |
        |        |   to MongoDB queries |                               |
        |        +----------------------+                               |
        |                               |                               |
        |        +----------------------+                               |
        |        | DatabaseHandler      |                               |
        |        | - Executes queries   |                               |
        |        | - Fetches results    |                               |
        |        +----------------------+                               |
        |                               |                               |
        |        +----------------------+                               |
        |        | ResponseGenerator    |                               |
        |        | - Summarizes results |                               |
        |        | - Crafts replies     |                               |
        |        +----------------------+                               |
```


---

## Dataset Used

This project uses the MongoDB Atlas Sample Analytics Dataset, which simulates a financial services application.

- **Database name:** `sample_analytics`
- **Collections:**
    - `accounts`: Account details for users.
    - `customers`: Customer details and their accounts.
    - `transactions`: Transaction records for accounts.

**Sample documents and schema details:**
See the [official MongoDB documentation](https://www.mongodb.com/docs/atlas/sample-data/sample-analytics/) for structure and examples.

**How to load the dataset:**

1. Sign up for a free [MongoDB Atlas](https://www.mongodb.com/atlas/database) account.
2. [Follow these instructions to load the sample dataset into your cluster.](https://www.mongodb.com/docs/atlas/sample-data/)

---

## Setup \& Implementation in Notebook

### 1. **Install Required Libraries**

Add this cell at the top of your notebook:

```python
!pip install --upgrade google-generativeai gradio pymongo nltk
```


### 2. **Download NLTK Data**

If using NLTK stopwords, run:

```python
import nltk
nltk.download('stopwords')
```


### 3. **Set Up API Keys and Database Connection**

- **Google Gemini API Key:**
Get your API key from [Google AI Studio](https://aistudio.google.com/app/apikey).
You can set it as an environment variable or enter it when prompted in the notebook.
- **MongoDB Atlas Connection String:**
Get your connection string from your [MongoDB Atlas dashboard](https://cloud.mongodb.com/).
Make sure your database contains the `sample_analytics` dataset.


### 4. **Load the MongoDB Sample Analytics Dataset**

- Go to your MongoDB Atlas cluster.
- Click "Load Sample Dataset" (this will add `sample_analytics` with `accounts`, `customers`, and `transactions` collections).
- [Official MongoDB instructions here.](https://www.mongodb.com/docs/atlas/sample-data/)


### 5. **Run the Notebook Cells**

- Execute each cell in order (configuration, class definitions, Gradio interface, etc.).
- When you reach the Gradio launch cell, a link will appear—click it to open the chat interface.

---

## Usage

- Type a question about the database (e.g., "Show all customers from New York" or "What is the total transaction amount in London last month?").
- The agent will reply conversationally and remember previous queries for context.

---



## Dataset Download Link

- [MongoDB Sample Analytics Dataset Documentation \& Download](https://www.mongodb.com/docs/atlas/sample-data/sample-analytics/)

---

**Enjoy exploring your MongoDB data with conversational AI!**

<div style="text-align: center">⁂</div>
