
## Building Your Own YouTube Search Application

---

### Generate Your YouTube Data API Key

1. Go to the [Google Developer Console](https://console.developers.google.com/).
2. Next to the Google Cloud Platform logo, click on your current project.
3. In the modal that appears, you'll see a list of your existing projects.
4. Click on "New Project" at the top to create a new project.
5. Choose a name for your project and click "Create Project."
6. After the project is created, navigate to the "Enable APIs and Services" tab in the dashboard.
7. Look for the "YouTube Data API" and enable it.
8. Proceed to the "Credentials" section and generate an API key.

### Setting Up the Django Environment and Basic Configuration

1. Open your preferred terminal or command prompt and navigate to the desired folder.
2. Use the following command to create a virtual environment (replace "myvenv" with your chosen name):
   ```
   python -m venv myvenv
   ```
3. Activate the virtual environment using this command:
   ```
   source myvenv/bin/activate   # On macOS/Linux
   myvenv\Scripts\activate      # On Windows
   ```
4. You'll see the environment name to the left of your command line if it's activated.
5. If you're using an older version of pip, upgrade it with:
   ```
   python -m pip install --upgrade pip
   ```
6. Create a "requirements.txt" file in the same folder.
7. Add the following lines to "requirements.txt":
   ```
   Django~=4.0
   requests~=2.26.0
   ```
8. Install all the required packages using this command:
   ```
   pip install -r requirements.txt
   ```

### Creating a Django App

1. Create your Django project with the following command:
   ```
   django-admin startproject ytsearchapi
   ```
2. Navigate into the project folder and create a new app for the search functionality:
   ```
   cd ytsearchapi
   python manage.py startapp ytsearch
   ```
3. Inside the "settings.py" file of your "ytsearchapi" project, add the "ytsearch" app to the "INSTALLED_APPS" list.
4. Start the development server by running:
   ```
   python manage.py runserver
   ```

### Designing Database Models for Storing Search Results

1. Open the "models.py" file inside the "ytsearch" folder and define the models for the database:
   ```python
   from django.db import models

   class SearchResults(models.Model):
       video_id = models.CharField(max_length=16, primary_key=True)
       title = models.CharField(max_length=255)
       description = models.TextField()
       search_query = models.CharField(max_length=120)
       publish_datetime = models.DateTimeField(null=True)
       thumbnail_url = models.JSONField(default=dict, null=True)

       def __str__(self):
           return self.video_id
   ```
2. Register the newly created model in the "admin.py" file to make it accessible in the admin dashboard:
   ```python
   from django.contrib import admin
   from .models import SearchResults

   admin.site.register(SearchResults)
   ```
3. Apply the model changes by creating and running migrations:
   ```
   python manage.py makemigrations
   python manage.py migrate
   ```
4. Access the admin panel by creating a superuser:
   ```
   python manage.py createsuperuser
   ```
5. Use the credentials to log in to the admin panel at "/admin" on your website.

---

