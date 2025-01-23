# 27.-CodeBuddy-Bot-Streamlit-Website
Add the description here  
add telegram bot code here too  
say refer to the other github repo for the telegram bot deployed place

mention about the secrets for the streamlit website how to do it, and where its kept (for the snowflake, and firebase api keys). Say the toml is just a txt file, and just need make the dict of the json file all straight and convert it to json format. Since the firebase.Certificate function takes in a JSON file/object??

This is how the secrets.toml file look like int he Streamlit cloud deployment platform of the streamlit web app's 'secrets' settings:
```text
SNOWFLAKE_ACCOUNT = "PCQBTTO-VK19305"
SNOWFLAKE_USER = "MEGIE"
SNOWFLAKE_PASSWORD = "M1stral!h4ck!"

FIREBASE_DB_CONVERSATIONS = '{"type": "service_account","project_id": "urop-telegram-chatbot","private_key_id": "teehee","private_key": "teehee","client_email": "teehee","client_id": "teehee","auth_uri": "teehee","token_uri": "teehee","auth_provider_x509_cert_url": "teehee","client_x509_cert_url": "teehee","universe_domain": "teehee"}'
FIREBASE_DB_ASSIGNMENTS = '{"type": "service_account","project_id": "urop-chatbot-assignments","private_key_id": "teehee","private_key": "teehee","client_email": "teehee","client_id": "teehee","auth_uri": "teehee","token_uri": "teehee","auth_provider_x509_cert_url": "teehee","client_x509_cert_url": "teehee","universe_domain": "teehee"}'
```

Initially firebase's api gave it like this, so you need remove all the \n (next lines) and make it into a straight line in order for this to work:
```text
{
  "type": "service_account",
  "project_id": "urop-telegram-chatbot",
  "private_key_id": "teehee",
  "private_key": "teehee",
  "client_email": "teehee",
  "client_id": "teehee",
  "auth_uri": "teehee",
  "token_uri": "teehee",
  "auth_provider_x509_cert_url": "teehee",
  "client_x509_cert_url": "teehee",
  "universe_domain": "teehee"
}
```

The Telegram chatbot autograder only works for Python,
and for code submitted that is wrapped in a function


Say this is the first time enabling the secret key? Or add this first time section to the 18. karoke event repo? (Might need redo the firebase key for that one also since that streamlit website also uses firebase integration)
From ChatGPT:
Me: How to jide api keys in github? I rmb you mentioned something like using environment varibales and the os library
ChatGPT said: To hide API keys in a GitHub project, you can use environment variables and the Python os library. Here's how:

Steps:
1. Create an .env File
In the root of your project, create a file named .env.
Store your API key in this file:
env
Copy
Edit
API_KEY=your_actual_api_key
2. Install python-dotenv
Install the library that helps load environment variables:
bash
Copy
Edit
pip install python-dotenv
3. Load the Environment Variable
In your Python code, use dotenv to load the .env file and access the API key:
python
Copy
Edit
from dotenv import load_dotenv
import os

# Load environment variables from the .env file
load_dotenv()

# Access the API key
api_key = os.getenv("API_KEY")
print(api_key)  # Test if it works
4. Add .env to .gitignore
Edit your .gitignore file and add .env to ensure it’s not pushed to GitHub:
bash
Copy
Edit
# Ignore environment variable file
.env
5. Set Environment Variables in Production
If deploying (e.g., to AWS, Heroku, Vercel), add the API_KEY as an environment variable in the platform’s settings.
Why This Works:
Environment Variables: Securely store sensitive information outside of your source code.
os Library: Allows your code to access environment variables easily.
.gitignore: Prevents the .env file from being tracked in version control.
Let me know if you’d like examples specific to your setup!


User: So lets say I use this. It will show in my github but the app will work if I deploy it?
ChatGPT said: If you use environment variables properly, your API key will not be visible in your GitHub repository, but your app will still work when deployed, provided you correctly configure the environment variables on the deployment platform.

Here’s how it works:

How It Works
On Your Local Machine

Your .env file contains sensitive data like API keys.
You add .env to .gitignore to ensure it isn’t pushed to GitHub.
Your app uses os.getenv() to fetch values from the .env file while running locally.
On GitHub

Since .env is ignored by Git, your repository will not contain the .env file.
Your API key or other sensitive information will remain hidden.
When Deploying Your App

Deployment platforms like Heroku, Vercel, AWS, Azure, etc., allow you to set environment variables in their dashboards.
Instead of reading from a .env file, your app will read these environment variables provided by the platform.
Example: Deploying to Heroku
1. Set Environment Variables on Heroku:
Go to the Settings tab of your Heroku app.
Click Reveal Config Vars.
Add your environment variables, e.g., API_KEY=your_actual_api_key.
2. Use the Same Code:
Your app will fetch the API_KEY using os.getenv("API_KEY").
No code changes are required because os.getenv works both locally and in production.
Security
Your API key never appears in your GitHub repository.
Deployment platforms handle environment variables securely, ensuring the key is injected at runtime.
Would you like help with setting up environment variables on a specific platform?
