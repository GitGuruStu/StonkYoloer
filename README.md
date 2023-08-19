# StonkYoloer
From real-time stock data to trend predictions, this collection of scripts and algorithms opens doors to better understanding and successful trading strategies. Dive into the world of finance armed with data, and elevate your trading game with StonkYoloer. Your journey to financial expertise starts here.



##LIST OF COMMANDS:
Provide a list of 50 keywords.
Create a macro to automate the process.
Macro: Copy the keyword and paste it into Google.
Apply news and 24-hour filters.
Open all resulting articles.
Copy text from each article.
Paste articles into ChatGPT.
Provide a prompt for ChatGPT.
Macro: Prompt ChatGPT for each article.
Copy ChatGPT's results.
Paste ChatGPT's results into Excel.
Set up daily repetition of this process.






##GOAL 1: Build a Macro that can link a spreadhseet to google search engine. 

I'm excited to have you on board! Let me give you an overview of our first goal, which is to build an essential macro that will significantly enhance our data analysis capabilities.

GOAL 1: Automating Data-Driven Insights

Our objective here is to create a macro that streamlines the entire process of gathering and analyzing news data related to specific keywords. Here's a breakdown of the steps we're aiming to achieve:

Linking Spreadsheet and Google Search:
We'll start by connecting a spreadsheet to the Google search engine. This will allow us to efficiently input and manage a list of 50 keywords directly from the spreadsheet.

Automation with Macro:
We'll develop a macro, a scripted automation tool, to carry out the following tasks seamlessly.

Keyword Search and Filters:
The macro will copy each keyword and initiate a search on Google. It will then apply filters to narrow down results to news articles and those published within the last 24 hours.

Article Retrieval:
The macro will open each resulting news article, extract the text content, and store it for further analysis.

Leveraging ChatGPT:
We'll integrate ChatGPT, a language model, to process the extracted article content. Each article's text will be provided as input to ChatGPT to generate insightful analyses.

Customized Prompts:
Before feeding articles to ChatGPT, the macro will also provide specific prompts to guide its analysis and ensure relevant outputs.

Automation with ChatGPT:
The macro will prompt ChatGPT for each article, generating comprehensive insights automatically.

Result Collection:
The generated insights from ChatGPT will be captured and organized, ready to be used for further analysis.

Seamless Integration with Excel:
The macro will paste the results from ChatGPT back into the Excel spreadsheet, ensuring easy access and reference.

Daily Repetition:
To enhance efficiency, we'll set up the macro to run this entire process on a daily basis, allowing us to stay up-to-date with the latest news insights effortlessly.







####I've been engaging with ChatGPT, and this is the code it recommended as a starting point for my studies.











import requests
from bs4 import BeautifulSoup
import time

# List of keywords
keywords = ["keyword1", "keyword2", ...]

# Your GPT-3 API key and endpoint
gpt_api_key = "your_gpt_api_key"
gpt_endpoint = "https://api.openai.com/v1/engines/davinci-codex/completions"

# Loop through keywords
for keyword in keywords:
    # Search Google News
    search_url = f"https://www.google.com/search?q={keyword}&tbm=nws&tbs=qdr:d"
    response = requests.get(search_url)
    soup = BeautifulSoup(response.text, "html.parser")
    
    # Extract article URLs
    article_links = [a['href'] for a in soup.find_all('a', {'class': 'VDXfz'})]
    
    # Loop through article links
    for link in article_links:
        # Open article and extract text
        article_response = requests.get(link)
        article_soup = BeautifulSoup(article_response.text, "html.parser")
        article_text = article_soup.get_text()  # Extract text
        
        # Set up GPT-3 prompt
        prompt = f"Keyword: {keyword}\nArticle:\n{article_text}\nPrompt:\n[Your Prompt]"
        
        # Make request to GPT-3
        gpt_input = {
            "prompt": prompt,
            "max_tokens": 100  # Adjust as needed
        }
        gpt_response = requests.post(gpt_endpoint, json=gpt_input, headers={"Authorization": f"Bearer {gpt_api_key}"})
        gpt_result = gpt_response.json()["choices"][0]["text"]
        
        # Paste GPT-3 results back into Excel or a file
        
        # Sleep to avoid overloading servers
        time.sleep(2)  # Adjust as needed
