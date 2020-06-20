# TrueCaller_REST_API

Coding Task

-> Create a REST api to be consumed by a mobile app, which is somewhat similar to TrueCaller (basically a combination of a global database of people and contacts along with spam detection). You can use whichever language/framework you're most comfortable in. However, we give strong preference to candidates in the pipeline who’ve done it using Django, and to a lesser extent Flask or Rails. For persistence you need to use a relational database along with an ORM for your framework. We will not evaluate NoSQL or raw SQL queries.

Terminology and assumptions:

-> Each registered user of the app can have zero or more personal “contacts”.
-> The “global database” is basically the combination of all the registered users and their personal contacts (who may or may not be registered users).
-> The UI will be built by someone else - you are simply making the REST API endpoints to be consumed by the front end.
-> You will be writing the code as if it’s for production use and should thus have the required performance and security. However, only you should use only a web server (the development server is fine) and a database, and just incorporate all concepts using these two servers. Do not use other servers.

Data to be stored for each user:

-> Name, Phone Number, Email Address.

Registration and Profile:

-> User has to register with at least name and phone number, along with a password, before using. He can optionally add an email address.
-> Only one user can register on the app with a particular phone number.
-> User needs to be logged in to do anything; there is no public access to anything.
-> You can assume that the user’s phone contacts will be automatically imported into the app’s database - you don’t need to implement importing the contacts.

Spam:

-> User should be able to mark a number as spam so that other users can identify spammers via the global database. Note that the number may or may not belong to any registered user or contact - it could be a random number.

Search:

-> User can search for a person by name in the global database. Search results display the name, phone number and spam likelihood for each result matching that name completely or partially. Results should first show people whose names start with the search query, and then people whose names contain but don’t start with the search query.
-> User can search for a person by phone number in the global database. If there is a registered user with that phone number, show only that result. Otherwise, show all results matching that phone number completely - note that there can be multiple names for a particular phone number in the global database, since contact books of multiple registered users may have different names for the same phone number.
-> Clicking a search result displays all the details for that person along with the spam likelihood. But the person’s email is only displayed if the person is a registered user and the user who is searching is in the person’s contact list.

Data Population:

-> For your testing you should write a script or other facility that will populate your database with a decent amount of random, sample data.



INSTALLATION

1) Unzip the compressed folder containing the application into a suitable directory of your choice.

2) Go to the unzipped folder and activate virtual environment:

Example for Windows : (I have my repository in "D:")

=> Type following commands in Command Prompt :

i) d:

ii) cd codingTask/codingTask

iii) .\Scripts\activate

3) Now go to apiTask folder which is in current directory to run our Django project.

=> Continue in Command Prompt where we left in step 2 :

iv) cd apiTask

v) python manage.py makemigrations

vi) python manage.py migrate

vii) python manage.py runserver

4) Take the HTTP address from the line beginning with "Starting development server at...".Put that web address into a web browser of your choice and go to it. The URL you enter should look something like this: http://127.0.0.1:8000

5) You now have the Django application running.

6) There will be no homepage at http://127.0.0.1:8000 , so you will get "Page not found" (404) Error!

=> Use https://jsonformatter.org/ to see proper json formatted output of our API

7) To access API , goto http://127.0.0.1:8000/api/ (It is general api displaying all our detail including users with it's contact and spamReports)

8) For searching use:

=> Search by name: http://127.0.0.1:8000/api/user/<name>

Example: http://127.0.0.1:8000/api/user/rajender

=> Search by Phone Number: http://127.0.0.1:8000/api/user/<phoneNumer>

Example:

-> Registered User: http://127.0.0.1:8000/api/user/9824650999

-> Unregistered User but in Contacts of Registered Users: http://127.0.0.1:8000/api/user/9824655999

Note:
=> Some data may be repetitive while searching in user's contacts as same dataset frequently used to populate contact's database.
