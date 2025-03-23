# 📊 CSV_Bot: AI-Powered CSV QnA Bot

## Overview
CSV_Bot is an AI-powered QnA bot that enables users to interact with CSV files using natural language queries. It leverages **Langchain**, **Google's Gemini API** for natural language processing, and **PandasAI** for intelligent data analysis and visualization. Users can retrieve insights and generate visualizations directly from their CSV data.

## 🚀 Features
- **Natural Language Queries**: Ask questions about the CSV file in plain English.
- **Automated Data Analysis**: Processes and analyzes data dynamically.
- **Data Visualization**: Automatically generates and displays plots for relevant queries.
- **Google Gemini Integration**: Utilizes Gemini for advanced language understanding.
- **PandasAI Integration**: Enables intelligent interactions with structured data.

## 🛠 Installation
Run the following commands in a Google Colab notebook:
```bash
!pip install pandasai[langchain] langchain_community pandas matplotlib google-generativeai
```

## 📌 Usage
1. **Load your CSV file:**
   ```python
   import pandas as pd
   from pandasai import SmartDataframe
   from pandasai.llm import GoogleGemini
   
   df = pd.read_csv("your_file.csv")
   llm = GoogleGemini(api_key="YOUR_GOOGLE_API_KEY")
   sdf = SmartDataframe(df, config={"llm": llm})
   ```

2. **Ask a question:**
   ```python
   response = sdf.chat("Compare the different types of meals")
   print(response)
   ```

3. **Handling Plots:**
   If a visualization is required, the bot will generate and save a chart. You can display it using:
   ```python
   from IPython.display import display, Image
   display(Image("/content/exports/charts/temp_chart.png"))
   ```

## 🔧 Troubleshooting
- **Ensure `GOOGLE_API_KEY` is set correctly**.
- If you encounter `ImportError: matplotlib is required`, reinstall it:
  ```bash
  !pip install --upgrade matplotlib
  ```
- If PandasAI shows restricted operations error, update dependencies:
  ```bash
  !pip install --upgrade pandasai
  ```

## ⚡ Challenge: Exploring Alternative Approaches
Initially, I attempted to use **Pinecone** as a vector database to upsert large datasets and perform retrieval-augmented generation (RAG). However, due to large dataset size constraints and **Gemini’s small context window**, my resources were exhausted. This led me to explore **CSV-based QnA**, which proved to be more efficient for structured data interaction. This experience expanded my understanding beyond vector databases, embeddings, and LLMs.

## 🚀 Future Enhancements
- Improve **caching mechanisms** for faster responses.
- Extend support for **more complex queries**.
- Experiment with **larger models** for better context handling.

---
This project showcases an innovative way to interact with structured data while overcoming limitations of traditional vector-based methods. 🚀
