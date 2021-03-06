Sample Rails client
=======================================

*Note*: this has not been updated to the newest version of Arecibo which means it will try and contact the main site. You'll need to alter it to point your server.

This is a specific Arecibo implementation for Ruby on Rails.

Installation
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Check out the Rails client from git.

Place *clients/trunk/rails/* into your vendor/plugins directory.

Add in the following two lines into your Rails environment settings, normally this would be config/environment.rb:

.. code-block:: ruby

    ARECIBO_ACCOUNT_NUMBER = 'yourpublicaccount'
    ARECIBO_RESULT_TEMPLATE = "layouts/arecibo"

Add the following into your application controller (controllers/application.rb):

.. code-block:: ruby

    def rescue_action(exception)
      report_to_arecibo(exception)
    end

And finally copy the file from arecibo/assets/arecibo.rhtml into app/views/layouts. This is so that once the error has been sent to Arecibo, an error page is rendered. You can change the ARECIBO_RESULT_TEMPLATE to point to an error file of your liking or simply change the one now in place.

Installation is now complete.

Requirements
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

* If you wish to use the HTTP transport, then the Rails process will need to be allowed to make HTTP posts to the Arecibo server.

Notes
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

* By default we set all 404 as priority 5, 500 as priority 1 and the rest as priority 3. This can be altered in the wrapper.py module.

* A UID is generated by Rails is passed on to Arecibo, meaning that by default: UID, IP, server, type, traceback, url, status, user_agent, server and priority are set.

* This uses the Ruby library which sets a 10 second time out.