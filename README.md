
## YouTube Search Automation

---

This project offers an API to retrieve the most recent videos from YouTube, sorted in reverse chronological order of their publishing date and time. The videos are fetched based on a given tag or search query, and the results are presented in a paginated format.

## Prerequisites

- The latest version of [Python](https://www.python.org/downloads/) is recommended.
- You need a valid [Google account](https://accounts.google.com/SignUp?hl=nn).
- Install the [Python Package Index](https://pip.pypa.io/en/stable/installation/) if not already done.

## Running the Project Locally

1. Clone the repository by executing the following command:

   ```
   git clone https://github.com/irsayvid/YTSearchAutomation.git
   ```

2. Learn how to [generate a YouTube Data API key](./DOCUMENTATION.md#GenerateYouTubedataAPIkey) and save the API key(s) in the `apikeys.json` file.

3. Set up a local environment and install the project's requirements within your virtual environment. Follow the instructions provided in the [documentation](./DOCUMENTATION.md).

4. Run the application using the following command:

   ```
   python manage.py runserver
   ```

### Available URLs and Responses

- `/`: Initiates a request to the API and stores 15 results in the database. The default search query is "chess," but you can modify it by changing the input in the search bar.

- `/fetchresults`: Displays all stored responses from the database in a tabular paginated format. Each page contains up to 8 responses.

- `/fetchresults/2/`: Displays responses present on page 2 (you can replace "2" with any valid page number). If the specified page number exceeds the maximum available pages, the last available page is displayed.

- `/fetchresults/chess/`: Displays responses filtered by titles and search queries containing the word "chess." The filter looks for partial matches in either the title or the search query.

- `/fetchresults/chess/3/`: Displays responses present on page 3, filtered by titles and search queries containing the word "chess." Similar to the previous case, it checks for partial matches in either the title or the search query.

Feel free to customize the search terms and adapt the code to suit your requirements.

---
