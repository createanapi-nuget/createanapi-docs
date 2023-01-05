Auth Repository Dashboard
==========================


Repositories are one of the CreateAnAPI Core resources, which is specialized database table that holds user login information. 

New Auth Repository
--------------------

You can create a new auth repository for an account in CreateAnAPI Admin.


.. image:: images/repository-1.png
   :width: 600

Auth Repository Name
""""""""""""""""""""""""

Auth Repository names are only used for users to identify the repository, it does not have any programatic impact and can be changed at any moment.

Registration Enabled
""""""""""""""""""""""""

Sets if the new user registration is enabled.

Registration Token Expiry In Hours
""""""""""""""""""""""""""""""""""""

Registration mail token expiration duration in hours.

Reset Password Enabled
""""""""""""""""""""""""

Sets if the forgot password process is enabled

Reset Password Token Expiry In Hours
""""""""""""""""""""""""""""""""""""""

Reset password mail token expiration duration in hours

Domains
""""""""""""""""""""""""

The domains of the authentication repository. 


.. Attention:: If registration or reset password process is enabled, username has to be email

.. Attention:: These options can be overriden in the code.