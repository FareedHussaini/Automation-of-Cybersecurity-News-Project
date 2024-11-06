<h1>Automation of Cybersecurity News with Python Script Project</h1>
<img src="https://imgur.com/DTMxOQ6.png" height="80%" width="80%" alt="diagram"/>

<h2>Description</h2>
In this project, I create a Python Script that parses through RSS feeds to automate the 5 most recent cybersecurity news from a list of popular cybersecurity websites. We code using Virtual Studio Code (any Python environment can be used) and a couple of libraries that you may need to import. Let's get right into this step-by-step guide!

<h2>Languages and Utilities Used</h2>
- <b>Python</b> 

<h2>Environments Used</h2>
- <b>Virtual Studio Code</b> (21H2)

<h2>Program Walk-Through:</h2>

<h3>Step 1: Setting Up the User Interface</h3>
Create a function with a menu for the user to select from a list of websites by inputting an integer value. The user can choose which website they would like to get cybersecurity news from:

```python
def show_menu():
    print("Choose a website to get recent news:")
    print("1. Website 1 - Example RSS")
    print("2. Website 2 - Example RSS")
    print("3. Website 3 - Example RSS")
    choice = int(input("Enter the number of your choice: "))
    return choice
This gives the user a choice to pick the website from which they want to view cybersecurity news.

<h3>Step 2: Parsing the RSS Feed</h3> The `feedparser` library is used to parse the selected website's RSS feed. Based on the input from the user, the function retrieves and formats the 5 most recent articles:
python
Copy code
def fetch_news(choice):
    urls = [
        "http://example.com/rss1",  # Replace with real RSS URLs
        "http://example.com/rss2",
        "http://example.com/rss3"
    ]
    
    feed = feedparser.parse(urls[choice - 1])
    
    articles = []
    for entry in feed.entries[:5]:
        articles.append((entry.title, entry.link))
    return articles
This step allows us to retrieve and store the top 5 most recent articles from the selected website.

<h3>Step 3: Displaying the Articles</h3> The articles are then displayed to the user with the title and link:
python
Copy code
def display_articles(articles):
    print("\nHere are the 5 most recent articles:")
    for i, (title, link) in enumerate(articles, start=1):
        print(f"{i}. {title}")
This step formats the output for easy viewing of the article titles.

<h3>Step 4: Opening the Selected Article</h3> When the user wants to open one of the articles, they input a number (1-5). The program uses the `webbrowser` library to open the corresponding article:
python
Copy code
def open_article(articles):
    choice = int(input("\nEnter the number of the article you want to open (1-5): "))
    webbrowser.open(articles[choice - 1][1])  # Open the selected article link
This step opens the article in the web browser, making it easy for the user to read.

<h3>Step 5: User-Friendly Formatting</h3> The script is structured to be user-friendly by repeatedly asking if the user wants to view another article or exit the program:
python
Copy code
def main():
    while True:
        choice = show_menu()
        articles = fetch_news(choice)
        display_articles(articles)
        open_article(articles)

        cont = input("\nDo you want to view another article? (y/n): ")
        if cont.lower() != 'y':
            break
This ensures that the user can keep browsing through articles or exit the script as desired.

<h3>Step 6: Running the Script</h3> To run the script, simply execute the following command in your terminal:
bash
Copy code
python automation_of_cybersecurity_news.py
<h2>Output:</h2> After making a choice, the program will list the 5 most recent articles. You will then be prompted to choose which article to open. Once you make your selection, it will open the article in your default web browser. <h2>Conclusion</h2> This concludes the Automation of Cybersecurity News with Python Script Project! You can add more features to this project, such as adding more websites to the list, fetching more articles, or even making the script more interactive. The same approach can also be used for automating other tasks!
<h3>Directory Structure (for your repository):</h3> ``` Cybersecurity-News-Automation/ │ ├── automation_of_cybersecurity_news.py # The Python script ├── README.md # Documentation for the project └── requirements.txt # List of Python dependencies (e.g., feedparser) ``` <h2>Additional Notes:</h2> - **Dependencies**: The script requires the `feedparser` library for parsing RSS feeds and the `webbrowser` library to open articles. To install the required dependencies, run: ```bash pip install -r requirements.txt ``` where `requirements.txt` contains: ``` feedparser ``` <h3>Running the Script:</h3> After running the script, the user will see the latest cybersecurity news, which they can view by selecting an article number.
<h2>Extending the Project (Optional):</h2> - Add more websites by adding their RSS URLs to the `urls` list in the `fetch_news()` function. - Fetch more than 5 articles or display additional information about each article (e.g., author, date). - Create a user interface or web app to make it more interactive.
With this full guide and code, you are ready to set up, run, and extend the Automation of Cybersecurity News project in your repository! Happy coding!
