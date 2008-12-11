This directory contains the PHP code you need to make phpBB recognise users who
are logged into your website using Django.  There are three files:

* getdjangouser.php.  This file provides a function that returns the Django
  username of the logged in user, or null if no-one is logged in.

* auth_django.php.  This file uses getdjangouser.php to  make all of your
  Django users into valid phpBB users.  If someone logs into your site using
  Django, then goes to your forums for the first time, they will be
  automatically registered and logged in to the forums.  When they visit in
  the future, if they are logged into your Django installation they will
  also be logged into phpBB.

* login_body.html.  This is a simple replacement for the login template so that
  when people would normally be presented with a page telling them to log into
  phpBB, they will instead be given a link telling them to log into your
  Django installation.

-------------------------------------------------------------------------------

In order to use these:

1. Put getdjangouser.php somewhere on your PHP include path.  Modify it to set
   the DBUSERNAME, DBPASSWORD, and DATABASENAME to match the settings for your
   Django installation.
2. Put auth_django.php inside your phpBB installation, under includes/auth.
3. Modify the links to the login and register pages inside login_body.html to
   match the appropriate ones for your Django installation, then use it to
   replace the login_body.html associated with your current phpBB style
   (probably in styles/something/template).
4. Make sure you have a Django user who has the same username as an
   administrator of the phpBB forums.
5. Log into Django as that user.
6. Log into phpBB as that user.
7. Use the phpBB administration panel to set the authentication module to
auth_django.

That should do the trick!


-------------------------------------------------------------------------------

Any problems?  Let us know at

    django-php-auth@resolversystems.com

