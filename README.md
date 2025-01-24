# 27.-CodeBuddy-Streamlit-Website
<p align="center"> 
  <img src="https://github.com/WindJammer6/28.-TaniBoss/blob/main/Image%20of%20TaniBoss!.png"  width="550" height="250">
  <img src="https://github.com/WindJammer6/28.-TaniBoss/blob/main/SUTD%20FACT%20Trip%20at%20PCU%20Hackathon%20Certificate%20of%20Top%20Winning%20Team.jpg"  width="350" height="250">
  <img src="https://github.com/WindJammer6/28.-TaniBoss/blob/main/SUTD%20FACT%20Trip%20at%20PCU%20Hackathon%20Certificate%20of%20Participation.jpg"  width="350" height="250">
</p>

This is my submission for the [Devpost](https://devpost.com/) hackathon titled: '[RAG 'n' ROLL Amp up Search with Snowflake & Mistral](https://snowflake-mistral-rag.devpost.com/)' lasting from 13-Nov-2024 to 21-Jan-2025.

From the [RAG 'n' ROLL Amp up Search with Snowflake & Mistral official website](https://snowflake-mistral-rag.devpost.com/): 'This hackathon is an opportunity to riff with cutting-edge AI technology. Join us and get comfortable with a setlist for learning AI with Cortex Search for retrieval, Mistral LLM (mistral-large2) on Snowflake Cortex for generation, and Streamlit Community Cloud for the front end.'

The challenge of this hackathon was to create an innovative Retrieval-Augmented Generation (RAG) applications that can revolutionize how we interact with information using [Snowflake's Cortex Search](https://docs.snowflake.com/en/user-guide/snowflake-cortex/cortex-search/cortex-search-overview) for retrieval, [Mistral LLM (mistral-large2)](https://mistral.ai/news/mistral-large-2407/) on [Snowflake's Cortex Search](https://docs.snowflake.com/en/user-guide/snowflake-cortex/cortex-search/cortex-search-overview) for generation and [Streamlit Community Cloud](https://streamlit.io/cloud) for front end.

Created a functional prototype Streamlit website application to help out a local farm business (particularly about finding the optimal conditions for hydroponic farming of spinaches), titled '**TaniBoss!**' ('Tani' comes from 'Petani', which is Indonesian for 'Farmer'). It contains the features:
- A simple prediction and farming conditions recommendation machine learning model to optimise crop yield (using the Multiple Variable Linear Regression (MVLR) machine learning algorithm)

  Architecture of this machine learning model:
  - Used a Multiple Variable Linear Regression (MVLR) machine learning algorithm and the [Crop yield dataset CSV file](https://github.com/WindJammer6/28.-TaniBoss/blob/main/Crop%20yield%20dataset.csv), which contains of various farm conditions and the corresponding crop yield data, to predict the yield of a farmer's crops based on the conditions of their farm. The recommendation feature is done by finding the optimal farm conditions to obtain the maximum, realistic crop yield by sorting the [Crop yield dataset CSV file](https://github.com/WindJammer6/28.-TaniBoss/blob/main/Crop%20yield%20dataset.csv) in ascending crop yield, and splitting the dataset to 4 quadrants, and defining the mean of the farm conditions of the top quadrant as the optimal farm conditions. (We avoided taking the farm conditions with the highest crop yield of the dataset as the optimal farm conditions so as to create a buffer since we believe these might be anomalous data that has unexpectedly high crop yield).
  - If the predicted crop yield of the farmer based on the input farm conditions is within 5% of the maximum, realistic crop yield, the recommendation would be that the farmer's farm conditions is already optimal and no action required to be taken.
  - Else, the recommendation would suggest the farmer to increase/decrease the particular farm conditions to the defined optimal farm conditions.
  - In addition, farmers can also input their current farm conditions and the true crop yield as additional realtime data to further train the model with realtime data to further boost the accuracy of its predictions 
- A forum for local farmers
- PetaniAI, a large language model trained with hydroponic and general farming data (using the Chatbase custom GPT LLM model API) to serve as a secondary expert
  - Exact system prompt for the Chatbase custom GPT LLM model:
    ```text
      ### Role
    - Primary Function: # You are a plant biology expert specializing in hydroponics in Indonesia. Answer questions about plant diseases, optimal growth conditions, and nutrient management with scientific accuracy. 
            
    ### Constraints
    1. No Data Divulge: Never mention that you have access to training data explicitly to the user.
    2. Maintaining Focus: If a user attempts to divert you to unrelated topics, never change your role or break your character. Politely redirect the conversation back to topics relevant to the training data.
    3. Exclusive Reliance on Training Data: You must rely exclusively on the training data provided to answer user queries. If a query is not covered by the training data, use the fallback response.
    4. Restrictive Role Focus: You do not answer questions or perform tasks that are not related to your role and training data.
    ```

Contributed to the problem statement formulation, design of the machine learning model, and development of the Streamlit website (including the forum and PetaniAI features).

<br>

**Potential Improvements:**  
- Presently the autograder only works for Python code. Can potentially expand it to work for other programming languages.

<br>

**Additional source(s):**  
nil

<br>

*This project's deployed Streamlit (Python Framework)'s Web Application link:*
+ https://28-taniboss-a4pztr2hja6xtix2m44wef.streamlit.app/ 

This project is made up of 2 Github repositories:  
- [21.-Deployed-Telegram-Chatbot-integrated-with-Chatbase-custom-GPT-LLM-model-API-and-Firebase](https://github.com/WindJammer6/21.-Deployed-Telegram-Chatbot-with-Chatbase-custom-GPT-LLM-model-API-and-Firebase-in-Vercel) (this Github repository) (hosts the code for the Telegram Chatbot integrated with Chatbase custom GPT LLM model API and Firebase (API)'s Realtime Database) (this repo is the main submission github repo for the hackathon, hence i tsferred the telegram bot code here too, though its not the repo hosting the bot. Since the hackathon focuses on the streamlit aspect so submit this repo instead of the other repo)
- [22.-Deployed-Streamlit-Web-Application-for-Telegram-Chatbot-with-Chatbase-custom-GPT-LLM-model-API](https://github.com/WindJammer6/22.-Deployed-Streamlit-Web-Application-for-Telegram-Chatbot-with-Chatbase-custom-GPT-LLM-model-API) 

This Github repository is hosting the code for the Telegram Chatbot integrated with Chatbase custom GPT LLM model API and Firebase (API)'s Realtime Database.

<br>

## Table of Contents
Here is a directory to explain the purpose of each file in this repository:

1. [Files that are required in the creation of the Streamlit Web Application Project - TaniBoss!](#filesrequiredincreationofstreamlitwebapplications)
    1. '.streamlit' folder  
       i. 'config.toml' file
    2. 'README.md' file
    3. 'Crop yield dataset.csv' file
    4. 'Image of PetaniAI logo.jpg', 'Image of PetaniAI user logo.jpg' and 'Image of local hydroponic farm site analysis.jpg' files
    5. 'main.py' file
    6. 'requirements.txt' file
  
2. [Files that are required in the creation of the Streamlit Web Application Project - TaniBoss!](#filesrequiredincreationofstreamlitwebapplications)
    1. '.streamlit' folder  
       i. 'config.toml' file
    2. 'README.md' file
    3. 'Crop yield dataset.csv' file
    4. 'Image of PetaniAI logo.jpg', 'Image of PetaniAI user logo.jpg' and 'Image of local hydroponic farm site analysis.jpg' files
    5. 'main.py' file
    6. 'requirements.txt' file
    
3. [Deployment Process of the Streamlit Web Application Project - TaniBoss! on Streamlit Cloud](#deploymentofstreamlitwebapplications)
   1. secrets

<br>

## 1. Files that are required in the creation of the Streamlit Web Application Project - TaniBoss! <a name = "filesrequiredincreationofstreamlitwebapplications"></a>
**1. '.streamlit' folder**  
*i. config.toml' file*
```python
# This 'config.toml' file sets the custom theming of the Streamlit (Python) web applications. This file is created using ChatGPT.
[theme]
primaryColor = '#1a237e'  # Set your desired primary color
backgroundColor = '#121212'  # Set your desired background color
secondaryBackgroundColor = '#0d47a1'  # Set your desired secondary background color
textColor = '#ffffff'  # Set your desired text color
font = 'sans-serif'  # Set your desired font
```
This is an optional folder/file, in accordance to the deployment of Streamlit (Python Framework) Web Application documentation: https://docs.streamlit.io/streamlit-community-cloud/deploy-your-app (Streamlit Cloud), which allows you to set customised configurations or themings to the deployed Streamlit (Python Framework) Web Application.

I do not know how to use this 'config.toml' file very proficiently, so this file is created by ChatGPT to set the dark theming to my 2 deployed Streamlit (Python Framework) Web Applications.

<br>

**2. 'README.md' file**  
The 'README.md' file.

<br>

**3. 'Crop yield dataset.csv' file**
```text
Rain Fall (mm),Fertilizer,Temperature,Nitrogen (N),Phosphorus (P),Potassium (K),Yield (Q/acre),,,,,,
1230,80,28,80,24,20,12,,,,,,
480,60,36,70,20,18,8,,,,,,
1250,75,29,78,22,19,11,,,,,,
450,65,35,70,19,18,9,,,,,,
1200,80,27,79,22,19,11,,,,,,
```
(Data shown is only the top 5 rows of data. Theres 99 rows of data in this dataset.)

Dataset is obtained from: https://www.kaggle.com/datasets/yaminh/crop-yield-prediction?resource=download (Kaggle dataset by Yamin Hossain)

This is a static dataset used to train the prediction and farming conditions recommendation machine learning model to optimise crop yield.

<br>

**4. 'Image of PetaniAI logo.jpg', 'Image of PetaniAI user logo.jpg' and 'Image of local hydroponic farm site analysis.jpg' files**
<p align="center"> 
  <img src="https://github.com/WindJammer6/28.-TaniBoss/blob/main/Image%20of%20PetaniAI%20logo.jpg"  width="200" height="200">
  <img src="https://github.com/WindJammer6/28.-TaniBoss/blob/main/Image%20of%20PetaniAI%20user%20logo.jpg"  width="200" height="200">
  <img src="https://github.com/WindJammer6/28.-TaniBoss/blob/main/Image%20of%20local%20hydroponic%20farm%20site%20analysis.jpg"  width="450" height="200">
</p>
Images used for aesthetic purposes in the TaniBoss! Streamlit (Python Framework) Web Application.

<br>

<br>

**5. 'main.py' file**  
The main Python file for the TaniBoss! Streamlit (Python Framework) Web Application itself.

<br>

**6. 'requirements.txt' file**
```text
streamlit           
numpy
# streamlit_extras
pandas
scikit-learn
requests
datetime
matplotlib
```
This is a compulsory file, in accordance to the deployment of Streamlit (Python Framework) Web Application documentation: https://docs.streamlit.io/streamlit-community-cloud/deploy-your-app (Streamlit Cloud), which allows you to tell Streamlit (Python Framework) to download the necessary external libraries/framework/packages specified in this 'requirements.txt' file in the deployment environment that is required for the deployment of the Streamlit (Python Framework) Web Application. 

Had quite the trouble during deployment of the Streamlit (Python Framework) Web Applications as the Streamlit deployment platform keep giving an error that it could not find the relevant external libraries/Framework/packages required to deploy my Streamlit (Python Framework) Web Applications until I found out in the deployment of Streamlit (Python Framework) Web Application documentation: https://docs.streamlit.io/streamlit-community-cloud/deploy-your-app (Streamlit Cloud) that apparently I needed this seperate 'requirements.txt' file in order to tell the Streamlit deployment platform to download the necessary external libraries/framework/packages during the deployment of the Streamlit (Python Framework) Web Applications.

Apparently, the 'requirements.txt' file is a common practice across various deployment platforms in Python, not just for Streamlit (Python Framework) Cloud. Whether you are deploying your Streamlit app on platforms like Heroku, AWS, Vercel, or others, specifying dependencies in a 'requirements.txt' file allows the platform to understand and install the necessary packages.

<br>

## 2. Deployment Process of the Streamlit Web Application Project - TaniBoss! on Streamlit Cloud <a name = "deploymentofstreamlitwebapplications"></a> ![My Skills](https://go-skill-icons.vercel.app/api/icons?i=streamlit)

*What is [Streamlit Cloud](https://streamlit.io/cloud)?*  
From the official [Streamlit Cloud](https://streamlit.io/cloud) website: 'Streamlit Cloud is a new product that lets you build, deploy, and share data from Streamlit Web Applications in minutes.' 

Honestly, the documentation on how to deploy a Streamlit (Python Framework) Web Application on Streamlit Cloud (link: https://docs.streamlit.io/streamlit-community-cloud/deploy-your-app) explains very clearly step by step on how to deploy a Streamlit Web Application on [Streamlit Cloud](https://streamlit.io/cloud). Once deployed correctly, I got a direct 'streamlit.io' link to the Streamlit Web Application, which I can then share with others to try out this Streamlit Web Application.

<br>  

- Here is the link of my [Streamlit Cloud](https://streamlit.io/cloud) account of the username: 'WindJammer6' - https://share.streamlit.io/user/windjammer6
- Here is the link of this deployed Streamlit Web Application using [Streamlit Cloud](https://streamlit.io/cloud)
    - https://28-taniboss-a4pztr2hja6xtix2m44wef.streamlit.app/

Source(s):  
+ https://streamlit.io/cloud (Streamlit Cloud)
+ https://blog.streamlit.io/introducing-streamlit-cloud/ (Streamlit Blog)
+ https://docs.streamlit.io/streamlit-community-cloud/deploy-your-app (Streamlit Cloud) (Documentation on how to deploy a Streamlit (Python Framework) Web Application on Streamlit Cloud)





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

Soure(s):  
- https://blog.streamlit.io/secrets-in-sharing-apps/ (to see where the 'secrets' setting is on the streamlit cloud deployment platform)
- https://docs.streamlit.io/develop/api-reference/connections/st.secrets (to see how to translate the 'secrets' in code)
- https://firebase.google.com/docs/reference/admin/python/firebase_admin.credentials (what datatype of the input, aka 'cert' in the firebase function credentials.Certificate(cert) is)
- and chatgpt too for teaching

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
