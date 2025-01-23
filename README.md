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
