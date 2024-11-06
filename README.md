# Automation of Cybersecurity News with Python Script Project
<img src="https://imgur.com/DTMxOQ6.png" height="80%" width="80%" alt="diagram"/>

## Description
In this project, we create a Python Script that parses through RSS feeds to automate the 5 most recent cybersecurity news from a list of popular cybersecurity websites. We code using Virtual Studio Code (any Python environment can be used) and a couple of libraries that you may need to import. This step-by-step guide will walk you through the process!

## Languages and Utilities Used
- **Python**

## Environments Used
- **Virtual Studio Code** (21H2)

## Program Walk-Through:

### Step 1: Setting Up the User Interface
We start by creating a function that will display a menu for the user to choose which website they want to get cybersecurity news from. The user can input an integer value to select from a list of websites.

```python
def show_menu():
    print("Choose a website to get recent news:")
    print("1. Website 1 - Example RSS")
    print("2. Website 2 - Example RSS")
    print("3. Website 3 - Example RSS")
    choice = int(input("Enter the number of your choice: "))
    return choice

```

This function gives the user a choice to pick which website to fetch news from by entering a number.

Step 2: Parsing the RSS Feed
We use the feedparser library to parse the selected website's RSS feed. Based on the user’s choice, the function retrieves and formats the 5 most recent articles.

```python
  
import feedparser

def fetch_news(choice):
    urls = [
        "http://example.com/rss1",  # Replace with real RSS URLs
        "http://example.com/rss2",
        "http://example.com/rss3"
    ]
    
    feed = feedparser.parse(urls[choice - 1])
    
    articles = []
    for entry in feed.entries[:5]:  # Retrieve top 5 most recent articles
        articles.append((entry.title, entry.link))
    return articles

```

This function parses the selected RSS feed and stores the title and link of the 5 most recent articles.

Step 3: Displaying the Articles
Once the news articles are fetched, we display them to the user. Each article will have a title and a corresponding link that the user can open.

```python

def display_articles(articles):
    print("\nHere are the 5 most recent articles:")
    for i, (title, link) in enumerate(articles, start=1):
        print(f"{i}. {title}")
```

This function prints the list of the 5 most recent articles from the selected website.

Step 4: Opening the Selected Article
The user can input a number (1-5) to choose which article they want to open. We use the webbrowser library to open the corresponding article in the web browser.

```python

import webbrowser

def open_article(articles):
    choice = int(input("\nEnter the number of the article you want to open (1-5): "))
    webbrowser.open(articles[choice - 1][1])  # Open the selected article link
```

This function will open the chosen article link in the default web browser.

Step 5: User-Friendly Formatting
To make the program more user-friendly, we structure it to repeatedly ask the user if they want to view another article or exit the program. This allows the user to easily navigate through the articles.

```python
def main():
    while True:
        choice = show_menu()  # Show the menu to the user
        articles = fetch_news(choice)  # Fetch the news from the selected site
        display_articles(articles)  # Display the list of articles
        open_article(articles)  # Open the selected article in the browser

        cont = input("\nDo you want to view another article? (y/n): ")
        if cont.lower() != 'y':  # Ask the user if they want to continue
            break
```

This is the main function that combines all the steps together. The user is continuously prompted to view more articles or exit the program.

Step 6: Running the Script
To run the script, execute the following command in your terminal:

python automation_of_cybersecurity_news.py
Output:
When the script runs, the user will be shown the 5 most recent articles from the selected website. The user will then be prompted to choose which article to open, and the article will open in the default web browser.

Conclusion
This concludes the Automation of Cybersecurity News with Python Script Project! You can extend this project by adding more websites, fetching more articles, or adding more interactive features. This same concept can also be applied to automate other tasks.
