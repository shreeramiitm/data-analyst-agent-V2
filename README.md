AI Data Analyst Agent
Overview
This project is a powerful, AI-driven Data Analyst Agent built with FastAPI and LangChain. It provides a REST API that can understand natural language instructions to perform complex data analysis tasks. The agent can source data from web pages, process and clean it, perform analysis, generate visualizations, and answer specific questions based on the findings.

The core of the agent is its modular workflow system, which intelligently selects and executes a series of steps to fulfill a user's request, from initial data scraping to final insight generation.

Key Features
Natural Language Understanding: Simply describe your data analysis task in a text file.

Multi-Modal Input: Accepts a required questions.txt file along with optional data files (e.g., CSVs, images).

Automated Web Scraping: Intelligently scrapes and parses data from web pages.

Data Cleaning & Processing: Automatically cleans and prepares data for analysis.

Advanced Analysis: Performs statistical analysis, identifies trends, and extracts key insights.

Dynamic Visualization: Generates charts and plots (e.g., scatterplots, histograms) and returns them as base64-encoded images.

Robust & Scalable: Built with a modern FastAPI backend and containerized with Docker for easy deployment.

Graceful Timeouts: Ensures a structured JSON response is always returned, even if a request exceeds the 5-minute processing limit.

Getting Started
Prerequisites
Python 3.10+

Docker

An LLM provider API key (e.g., OpenAI, Google Gemini)

Installation
Clone the repository:

git clone [your-github-repo-url]
cd [your-project-directory]

Create a virtual environment:

python -m venv venv
source venv/bin/activate  # On Windows, use `venv\Scripts\activate`

Install dependencies:

pip install -r requirements.txt

Configure Environment Variables:
Create a .env file in the project root and add your API keys.

AI_PIPE_TOKEN="your_openai_or_equivalent_api_key"
GOOGLE_API_KEY="your_google_api_key"

How to Run
Using Docker (Recommended)
Build the Docker image:

docker build -t data-analyst-agent .

Run the Docker container:

docker run -d -p 8000:80 --env-file .env --name data-agent-container data-analyst-agent

Running Locally
uvicorn main:app --host 0.0.0.0 --port 8000

The API will be available at http://localhost:8000.

API Usage
The primary endpoint is /api/. It accepts multipart/form-data POST requests.

Parameters:

questions_txt (required): A .txt file containing the natural language instructions for the analysis task.

files (optional): Additional files (e.g., data.csv, image.png) to be used in the analysis.

Example curl Request:

curl -X POST "http://localhost:8000/api/" \
-F "questions_txt=@path/to/your/questions.txt" \
-F "files=@path/to/your/data.csv"
