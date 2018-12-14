# django_helloworld
django try out hello world


Deploying a web app on PythonAnywhere involves pulling down your code from GitHub, and then configuring PythonAnywhere to recognise it and start serving it as a web application. There are manual ways of doing it, but PythonAnywhere provides a helper tool that will do it all for you. Let's install it first:

PythonAnywhere command-line
$ pip3.6 install --user pythonanywhere
That should print out some things like Collecting pythonanywhere, and eventually end with a line saying Successfully installed (...) pythonanywhere- (...).

Now we run the helper to automatically configure our app from GitHub. Type the following into the console on PythonAnywhere (don't forget to use your GitHub username in place of <your-github-username>, so that the URL matches the clone URL from GitHub):

PythonAnywhere command-line
$ pa_autoconfigure_django.py https://github.com/<your-github-username>/my-first-blog.git
As you watch that running, you'll be able to see what it's doing:

Downloading your code from GitHub
Creating a virtualenv on PythonAnywhere, just like the one on your own computer
Updating your settings file with some deployment settings
Setting up a database on PythonAnywhere using the manage.py migrate command
Setting up your static files (we'll learn about these later)
And configuring PythonAnywhere to serve your web app via its API
On PythonAnywhere all those steps are automated, but they're the same steps you would have to go through with any other server provider.

The main thing to notice right now is that your database on PythonAnywhere is actually totally separate from your database on your own computer, so it can have different posts and admin accounts. As a result, just as we did on your own computer, we need to initialize the admin account with createsuperuser. PythonAnywhere has automatically activated your virtualenv for you, so all you need to do is run:

PythonAnywhere command-line
(ola.pythonanywhere.com) $ python manage.py createsuperuser
Type in the details for your admin user. Best to use the same ones as you're using on your own computer to avoid any confusion, unless you want to make the password on PythonAnywhere more secure.

Now, if you like, you can also take a look at your code on PythonAnywhere using ls:

PythonAnywhere command-line
(ola.pythonanywhere.com) $ ls
blog  db.sqlite3  manage.py  mysite requirements.txt static
(ola.pythonanywhere.com) $ ls blog/
__init__.py  __pycache__  admin.py  forms.py  migrations  models.py  static
templates  tests.py  urls.py  views.py
You can also go to the "Files" page and navigate around using PythonAnywhere's built-in file browser. (From the Console page, you can get to other PythonAnywhere pages from the menu button in the upper right corner. Once you're on one of the pages, there are links to the other ones near the top.)
