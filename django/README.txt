This directory contains a Django application called sessionprofile.  Add it
to your project to make it maintain a table that maps sessions to user
objects.  This is useful when you want to access the current session's
Django user ID - for example, when you are integrating Django with phpBB.

The following instructions show how to create a minimal project that does
nothing but test this.

1. Create the project:

    django-admin.py startproject sessionprofile_test


2. Enable the admin GUI (to make testing easier) by uncommenting the
   appropriate lines in urls.py (three lines for Django 1.0) and adding

    'django.contrib.admin',

   to the INSTALLED_APPS in settings.py.


3. Copy the sessionprofile directory into the newly-created
   sessionprofile_test directory.


4. Modify settings.py:

    * Add appropriate settings for a database.

    * Add the line

        'sessionprofile.middleware.SessionProfileMiddleware',

      to your MIDDLEWARE_CLASSES, *before* SessionMiddleware.

    * Add the line

        'sessionprofile',

      to your INSTALLED_APPS.


5. Add the tables to your DB; run

    python manage.py syncdb

   ...creating an appropriate admin user.


6. Run the tests:

    python manage.py test


7. If they all pass, run the dev server:

    python manage.py runserver


8. Go to the admin pages at http://localhost:8000/admin/


9. In your DB, check the sessionprofile_sessionprofile table.
   You should have one session profile, with a null user.


10. Log in as your admin user.


11. In your DB, check the sessionprofile_sessionprofile table.
    You should have one session profile, associated with the
    admin user.


If you've got this far, everything is working fine and you
should be able to integrate the sessionprofile app with your
own project.

-------------------------------------------------------------------------------

Any problems?  Let us know at

    django-php-auth@resolversystems.com
