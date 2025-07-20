Health Care Center: AI-Powered Symptom Analysis and Health Guidance
Project Overview
The Health Care Center is a modern, interactive Single-Page Application (SPA) designed to assist users in understanding potential health concerns based on their symptoms and provide general health information using AI. It leverages a Flask backend for symptom prediction (simulated client-side for this SPA version) and integrates with the Google Gemini API for intelligent health-related Q&A and personalized tips.

This project aims to provide an intuitive and seamless user experience by consolidating all functionalities into a single page with tab-based navigation, eliminating traditional page reloads.

Features
Symptom Checker:

Interactive Multi-Select: Users can search for and select multiple symptoms from a predefined list using a dynamic dropdown.

Speech Recognition: Input symptoms using voice commands for enhanced accessibility.

Disease Prediction (Simulated): Based on selected symptoms, the system provides a simulated prediction of a potential disease, along with descriptions, precautions, medications, diets, and workouts.

AI Health Guidance (Powered by Google Gemini API):

General Health Questions: Ask any health-related question and receive an AI-generated answer.

Symptom Clarifier: Get concise, AI-generated explanations for specific symptoms, including common causes and implications.

Personalized Health Tips: Receive daily health tips, which can be tailored based on the last predicted disease for contextual relevance.

Single-Page Application (SPA):

Seamless navigation between "Symptom Checker", "About Us", "Blog", "Developer", and "Contact" sections without page reloads.

Responsive UI for optimal viewing on desktop, tablet, and mobile devices.

Technologies Used
Backend (Flask):

Python 3

Flask: Web framework for serving HTML templates and proxying API calls.

Pandas, NumPy, Scikit-learn: For data handling and the machine learning model (SVC) for disease prediction.

pickle: For loading the pre-trained machine learning model.

requests: For making HTTP requests to the Gemini API from the backend.

python-dotenv: For securely loading environment variables (like API keys) from a .env file.

Frontend (SPA - index.html):

HTML5

Tailwind CSS: For responsive and modern styling.

Vanilla JavaScript: For all interactive elements, dynamic content updates, multi-select dropdown logic, speech recognition, and API calls.

Google Gemini API: Accessed via the Flask backend for AI features.

Setup and Installation
Follow these steps to get the project up and running on your local machine.

1. Clone the Repository
(Assuming your project is in a Git repository. If not, just download the project files.)

git clone <your-repository-url>
cd <your-project-directory>

2. Backend Setup (Python/Flask)
a. Create a Virtual Environment (Recommended)
python -m venv venv

b. Activate the Virtual Environment
macOS/Linux:

source venv/bin/activate

Windows (Command Prompt):

venv\Scripts\activate.bat

Windows (PowerShell):

.\venv\Scripts\Activate.ps1

c. Install Dependencies
pip install Flask pandas numpy scikit-learn requests python-dotenv imblearn matplotlib seaborn

Note: imblearn, matplotlib, and seaborn are primarily for the Jupyter notebook for model analysis and are not strictly required for the Flask app to run, but good to have if you intend to work with the notebook.

d. Prepare Datasets and Model
Ensure you have the Datasets directory in your project root, containing:

symtoms_df.csv

precautions_df.csv

workout_df.csv

description.csv

medications.csv

diets.csv

svc.pkl (your trained SVC model)

These files are essential for the Flask backend to load and function correctly.

e. Configure Google Gemini API Key
Get an API Key:

Go to the Google Cloud Console.

Create a new project or select an existing one.

Navigate to "APIs & Services" > "Credentials".

Click "Create Credentials" > "API Key". Copy the generated key.

Important: Restrict your API key to prevent unauthorized use. Under "API restrictions," select "Generative Language API".

Enable the API: Ensure the "Generative Language API" is enabled for your project. You can do this by visiting the link provided in the error message if you encounter one (e.g., https://console.developers.google.com/apis/api/generativelanguage.googleapis.com/overview?project=<YOUR_PROJECT_NUMBER>).

Create .env file:

In the root directory of your project (where main.py is), create a new file named .env.

Add your API key to this file:

GEMINI_API_KEY="YOUR_API_KEY_HERE"

(Replace YOUR_API_KEY_HERE with the actual key you copied).

Add .env to .gitignore: To prevent committing your sensitive API key to version control, add the line /.env to your .gitignore file.

3. Frontend Setup (HTML/JavaScript)
The frontend is a single index.html file. Ensure it is located in your Flask app's templates folder (e.g., your_project/templates/index.html). The JavaScript within index.html is already configured to call your Flask backend's proxy endpoint (/api/gemini-ask), so no direct API key is needed in the frontend code.

How to Run the Application
Activate your virtual environment (if you haven't already).

Run the Flask application:

python main.py

You should see output indicating that the Flask development server is running, typically on http://127.0.0.1:5000/.

Access the Application:

Open your web browser and navigate to http://127.0.0.1:5000/.

Important: Do NOT open the index.html file directly from your file system, as the Flask templating and backend API calls will not work.

Project Structure
.
├── Datasets/
│   ├── symtoms_df.csv
│   ├── precautions_df.csv
│   ├── workout_df.csv
│   ├── description.csv
│   ├── medications.csv
│   ├── diets.csv
│   └── (other dataset files)
├── templates/
│   ├── index.html
│   ├── nav.html
│   ├── about.html
│   ├── blog.html
│   ├── contact.html
│   └── developer.html
├── static/
│   └── img.png
├── svc.pkl
├── main.py
├── Medicine Recommendation System.ipynb
└── .env
└── .gitignore

Future Improvements
Real-time Model Integration: Instead of a client-side simulation, integrate the actual Python svc.pkl model directly into the Flask backend's /predict endpoint to perform real machine learning predictions.

Model Accuracy:

Larger/More Diverse Dataset: Acquire and train the model on a significantly larger and more varied dataset of symptoms and diseases.

Advanced Feature Engineering: Explore more sophisticated ways to represent symptoms and patient data.

Deep Learning Models: Investigate using neural networks for potentially higher accuracy with larger datasets.

Confidence Scores: Implement confidence scores from the backend model to provide users with an indication of how certain the prediction is.

User Authentication/Profiles: Implement user accounts to save symptom history and personalized health tips.

Database Integration: Use a database (e.g., SQLite, PostgreSQL, Firestore) to store user data, feedback, or more extensive health information.

More Comprehensive AI Responses: Enhance prompts to Gemini API for more detailed or structured responses.

Interactive Visualizations: Incorporate Chart.js or Plotly.js for dynamic visualizations of health trends or symptom correlations (if relevant data is available).

Accessibility Enhancements: Further improve accessibility features beyond speech recognition.

Error Handling & User Feedback: More robust error messages and loading indicators for all API calls and predictions.

Disclaimer
This application is intended for informational and educational purposes only. The disease predictions provided are based on a simulated model and should NOT be considered professional medical advice. Always consult with a qualified healthcare professional for any health concerns or before making any decisions related to your health.