
AI-Diet-Coach 🏋️‍♀️🤖

Personalized Diet and Workout Recommendations powered by the Gemini API and Flask.

This project is a web application that takes detailed user input (dietary preferences, fitness goals, restrictions, and health conditions) and generates a comprehensive, structured health plan using Google's Gemini large language model.

✨ Features
Personalized Planning: Generates diet and workout plans tailored to specific user inputs (e.g., Vegetarian, Gluten-Free, Diabetes).
Structured Output: Uses advanced prompt engineering to ensure the Gemini model returns data in a parsable format (Diet Recommendations, Workout Options, Meal Suggestions, etc.).
Modern Python Stack: Built using Flask for the web interface and the official google-genai SDK for AI interaction.
Clean Interface: Simple web form for collecting user data and displaying recommendations.
🚀 Getting Started
Follow these steps to set up and run the application locally.

Prerequisites
You need the following installed:

Python 3.8+
A Gemini API Key. Get one from Google AI Studio.
Installation
Clone the repository:

git clone [https://github.com/YourUsername/Gemini-Fitness-Planner.git](https://github.com/YourUsername/Gemini-Fitness-Planner.git)
cd Gemini-Fitness-Planner
Create and activate a virtual environment (Recommended):

python -m venv venv
source venv/bin/activate  # On Linux/macOS
# .\venv\Scripts\activate   # On Windows
Install dependencies:

pip install -r requirements.txt
# If you don't have a requirements.txt, use:
# pip install flask google-genai
Configuration
Set Your API Key: The application requires your Gemini API Key to function. It's best practice to set this as an environment variable rather than hardcoding it into main.py.

Create a file named .env in the root directory and add your key:

# .env
GEMINI_API_KEY="YOUR_API_KEY_HERE"
Note: You would need to use a library like python-dotenv to load this key, but for simple deployment, you can keep the key directly in main.py for now, replacing the placeholder.

Update main.py (Temporary/Direct Method): Locate the API key line in main.py and replace the placeholder with your actual key:

# main.py
os.environ["GOOGLE_API_KEY"] = "your api" # Replace with your REAL key
Running the App
Execute the main Python file to start the Flask development server:

python main.py
Open your web browser and navigate to:
http://127.0.0.1:5000/

📂 Project Structure
The key files in this project are:

Gemini-Fitness-Planner/
├── main.py               # Main Flask application and Gemini API integration logic.
├── README.md             # This file.
├── requirements.txt      # List of Python dependencies (flask, google-genai).
└── templates/
    └── index.html        # HTML form for input and template for displaying results.
🧠 Core AI Logic (Documentation)
The core functionality resides in the generate_recommendation and recommendation functions in main.py.

1. Model Initialization
The application uses the stable and fast Gemini 2.5 Flash model for quick and high-quality responses:

Python

model = genai.GenerativeModel("gemini-2.5-flash")
2. Prompt Engineering
The generate_recommendation function uses a detailed, structured prompt to guide the model's output, ensuring all required sections are present and the response is easily parsable. Key instructions include:

Specifying all user constraints (e.g., "Gluten-Free, Lactose-Intolerant").

Explicitly asking for major sections: Diet Recommendations:, Workout Options:, Meal Suggestions: (separated into Breakfast and Dinner).

3. Data Parsing (Robustness)
The recommendation view function contains critical parsing logic to convert the raw text response from Gemini into a structured Python dictionary, handling potential variations in the model's output:

It uses specific string matching ("dinner options" in line_lower) to reliably switch between the breakfasts and dinners categories.

It only appends lines that start with list markers (1., *, -) to avoid capturing narrative text as recommendations.

🤝 Contributing
Feedback and contributions are welcome! Feel free to open issues or submit pull requests.## Color Reference
