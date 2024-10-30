# Django DB Demo

## Show empty SQLite db and after migrate  DEMO1

1.  mkdir <new folder name> - this is where your new project will be built
1.  `django-admin startproject demosite <folder name>`
1.  cd <new folder name> 
1.  `python manage.py runserver` 
1.  Open browser to localhost:8000 and show Successful install screen
1.  Open DB Browser For SQLite and select & show empty database
1.  `python manage.py migrate`
1.  Open database again and show that tables now exist

## Start a new app DEMO3

1.  python manage.py startapp <new app name> - for example: polls
1.  Comment: some background tasks have been done to views & urls & settings
1.  Open models.py
1.  Add models classes from tutorial
1.  Save file
1.  `python manage.py makemigrations polls`
1.  `python manage.py sqlmigrate polls 0001
1.  Comment: Here's the migration that was made. Note it's all SQL statements. The upper portion is the code for SQLite; the lower portion is code specific for PostgreSQL. So regardless of the db manager, you get the correct code.
1.  `python manage.py migrate`
1.  Open the database again and review the results

## Add some records in the shell DEMO4

1.  `python manage.py shell`
1.  Comment: created a superuser (admin) and added email & password (tIms2024pw)
1.  Comment: registered Question & Choice with polls/admin.py
1.  `python manage.py runserver`
1.  Go to localhost:8000/admin and login
1.  Select Question and add "What's up?" and save
1.  Select Choice and add Not Much, The Sky, Just Hacking linked to Question
1.  Optional: Add q's How's it going and Where are you going?
1.  Optional: Add choices

## View DB Again

1.  Open the database again and review the results - see all the added records
1.  Go back to models.py and make changes
1.  `python manage.py makemigration`
1.  `python manage.py migrate`
1.  Open the database again and review the added fields in Question

## Conclusion

*   We don't need to access the DB directly. Django will manage all db details instead of trying to straddle 2 environments (SQL & python)

*   DRY - Don't repeat yourself - all the db details in one place 

*   Database agnostic

*   Transfer database structure to production database server later. Don't need to worry about it now. 