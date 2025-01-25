# 27.-CodeBuddy-Streamlit-Website
<p align="center"> 
  <img src="https://github.com/WindJammer6/27.-CodeBuddy-Streamlit-Website/blob/main/Images%20for%20README/CodeBuddy_v3.jpg"  width="550" height="250">
  <img src="https://github.com/WindJammer6/27.-CodeBuddy-Streamlit-Website/blob/main/Images%20for%20README/Screenshot%202025-01-22%20013805.png"  width="350" height="250">
  <img src="https://github.com/WindJammer6/27.-CodeBuddy-Streamlit-Website/blob/main/Images%20for%20README/Screenshot%202025-01-22%20014313.png"  width="350" height="250">
</p>

This Github repository is my official submission for the [Devpost](https://devpost.com/) hackathon titled: '[RAG 'n' ROLL Amp up Search with Snowflake & Mistral Hackathon](https://snowflake-mistral-rag.devpost.com/)'. However, since my submission requires the deployment of 2 different applications, a Streamlit website (deployed using Streamlit Cloud) and a Telegram Bot (deployed using Vercel), I had to use 2 seperate Github repositories. Since according to the rules of the [RAG 'n' ROLL Amp up Search with Snowflake & Mistral Hackathon](https://snowflake-mistral-rag.devpost.com/), it requires the submission of a Streamlit website link and the Github repository hosting that Streamlit website, I decided to submit this Github repository as my official submission instead, while adding the main codes for the Telegram Bot in the folder '[telegram bot codes](https://github.com/WindJammer6/27.-CodeBuddy-Streamlit-Website/tree/main/telegram%20bot%20codes)'. You can see the Github repository hosting the Telegram Bot [here](https://github.com/WindJammer6/26.-CodeBuddy).

From the [RAG 'n' ROLL Amp up Search with Snowflake & Mistral official website](https://snowflake-mistral-rag.devpost.com/): 'This hackathon is an opportunity to riff with cutting-edge AI technology. Join us and get comfortable with a setlist for learning AI with Cortex Search for retrieval, Mistral LLM (mistral-large2) on Snowflake Cortex for generation, and Streamlit Community Cloud for the front end.'

The challenge of this hackathon was to create an innovative Retrieval-Augmented Generation (RAG) applications that can revolutionize how we interact with information using [Snowflake's Cortex Search](https://docs.snowflake.com/en/user-guide/snowflake-cortex/cortex-search/cortex-search-overview) for retrieval, [Mistral LLM (mistral-large2)](https://mistral.ai/news/mistral-large-2407/) on [Snowflake's Cortex Search](https://docs.snowflake.com/en/user-guide/snowflake-cortex/cortex-search/cortex-search-overview) for generation and [Streamlit Community Cloud](https://streamlit.io/cloud) for front end.

<br>

- Devpost link to the project 'CodeBuddy' in the [RAG 'n' ROLL Amp up Search with Snowflake & Mistral Hackathon](https://snowflake-mistral-rag.devpost.com/): https://devpost.com/software/codebuddy-bot?ref_content=my-projects-tab&ref_feature=my_projects

<br>

## Integration of Retrieval-Augmented Generation (RAG) using Snowflake Cortex Search and MistralAI LLM
This is the main code that integrates RAG using Snowflake Cortex Search and MistralAI LLM in the '[telegram_bot.py](https://github.com/WindJammer6/27.-CodeBuddy-Streamlit-Website/blob/main/telegram%20bot%20codes/telegram_bot.py)' file in the '[telegram bot codes](https://github.com/WindJammer6/27.-CodeBuddy-Streamlit-Website/tree/main/telegram%20bot%20codes)' folder.
```python
model = "mistral-large-latest"

client = Mistral(api_key=api_key)
```

```python
    conversation_history_and_other_data = client.chat.complete(
        model= model,
        messages = [
            {
                "role": "user",
                "content": f"""
                Assignment name: {CONVERSATION_INFORMATION['assignment']}
                Please provide me feedback of my submitted code according to the assignment notes without giving me the exact answer: {snowflake_cortex_search(CONVERSATION['assignment'])}
                Submitted code: {update.message.text}
                """,
            },
        ]
    )
```

The custom 'snowflake_cortex_search' Python function can be found in the '[snowflake_cortex_search.py](https://github.com/WindJammer6/27.-CodeBuddy-Streamlit-Website/blob/main/telegram%20bot%20codes/snowflake_cortex_search.py)' file in the '[telegram bot codes](https://github.com/WindJammer6/27.-CodeBuddy-Streamlit-Website/tree/main/telegram%20bot%20codes)' folder.

<br>

## From the 'About Project' section in the Devpost project submission of CodeBuddy:  
### Inspiration
Starting out into the programming world can be tricky for new programmers, even with the help of teachers in schools due to the lack of immediate feedback whenever they run into trouble during coding.

In Singapore, most programmers start out programming in university. At the same time, most students in university communicate via Telegram with their peers and professors. This calls for a dire need for a convenient and personalised coding assistant that can provide easy to understand, immediate feedback to the novice programmers' code answers to school assignments based on the school's notes to smoothen the start of their programming journey in school.

With these knowledge, along with the rise in popularity of LLMs such as ChatGPT, we were inspired to create CodeBuddy.

#### What it does
CodeBuddy is a Telegram Chatbot (deployed on Vercel) that leverages on the power of Retrieval-Augmented Generation (RAG) using Mistral LLM and Snowflake Cortex Search as the core backend engine that allows novice programmers to get instant feedback for errors/quality of their code for their school assignments based on the given school notes before submission to their respective school assignment submission portals. In addition, it allows course instructors/teachers to upload their assignments and notes for each assignment, as well as review conversations between the students and the Telegram Chatbot (as teaching review to what troubles the students are facing) via a Streamlit website.

#### How we built it
1. We first created a simple Telegram Bot using Telegram's BotFather.
2. Information of the selected assignment and code submitted by the assignment is passed through the Snowflake Cortex Search to retrieve the corresponding assignment notes and test cases of the selected assignment. The retrieved data, in addition to the initial information of the selected assignment and code submitted, will then be passed through the Mistral Large 2 LLM to generate the personalised, immediate feedback of the Telegram Bot to the user's code (Retrieval-Augmented Generation (RAG)). CodeBuddy also has a built-in autograder to calculate the score of the submitted code.
3. We created 2 seperate Firebase realtime databases, one realtime database that stores messages sent by the user and responses from the Telegram Bot and another realtime database that stores school assignments and notes for each assignment that teachers will be uploading via a Streamlit website.
4. With the help of Figma for the design prototype of the website, we created a Streamlit website that displays these conversations between the user and responses from the Telegram Bot. This website also allows teachers to upload their assignments and notes for each assignment.

#### Challenges we ran into
- We were unfamiliar with some of the technology, especially with the concept of Retrieval-Augmented Generation (RAG), we spent much time trying to understand it deeply
- Design of the software architecture was tricky in order to tackle the problem statement elegantly as we had to account for its usability for multiple stakeholders such as the students, the teachers and the school.
- Done at a seperate prototype iteration, we played around with OpenAI's LLM via its API. While it was very easy to use, we quickly realised the issue of privacy as we will be feeding confidential school assignments and notes into the LLM.

#### Accomplishments that we're proud of
With much less computational power, CodeBuddy works on par with popular LLMs such as ChatGPT and Gemini 

(We would like to test this using TruLens for comparison but we were unable to find the time to do the experiments. However, we tried to use OpenAI's API and we noticed that the autograding on both CodeBuddy and popular LLMs worked similarly, and also received feedback from new programmers that both popular LLM's and CodeBuddy's feedback were equally helpful, with some new programmers even saying that CodeBuddy's feedback is better since it is more personalised and specialised according to their school's teaching style, based on its assignments and notes)

#### What we learned
On a more personal note, we learned various complex concepts such as RAG and LLMs as well as some of the technologies used in this project such as Telegram Bot, Streamlit and Figma.

#### What's next for CodeBuddy
We see various possible expansion of CodeBuddy, 
- We hope to promote our project to universities around the world, specifically targeting beginner courses on programming in these schools. 
- While the Telegram Chatbot aspect of our project is highly accessible, user-friendly and free to anyone around the world as long as they have the Telegram app, we forsee that the database used will likely to be very large, and its size will exceed any free database subscriptions available online. Hence, we would require sponsors to maintain the database. Some possible partnerships could be government funding such as from the National Science Foundation (NSF), or corporate sponsorships such as from BairesDev and Klaviyo.
- CodeBuddy can be generalised for beginners in other fields of study other than programming. An example would be to the field of mathematics (which might require using another LLM that is fine-tuned for mathematics such as MathGPT) or the field of humanities.
