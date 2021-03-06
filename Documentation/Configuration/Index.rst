.. ==================================================
.. FOR YOUR INFORMATION
.. --------------------------------------------------
.. -*- coding: utf-8 -*- with BOM.

.. include:: ../Includes.txt


.. _configuration:

Configuration
=============

Checking the installation
-------------------------

Before you start configuring this extension, make sure that the Shibboleth environment is operational.
You can do so by creating a sub directory (say "securetest") within your document root and putting two files in there:

.htaccess
^^^^^^^^^

.. code-block:: none

	AuthType shibboleth
	ShibRequestSetting requireSession 1
	require valid-user

index.php
^^^^^^^^^

.. code-block:: none

	<?php
		phpinfo();
	?>

If you now direct your browser to https://yourdomain/securetest/ you should be redirected to your Shibboleth login page.
After logging in, you should be redirected to your web instance and see the output of the phpinfo() function.
Now, scroll down to the section "Apache Environment" and check, if you can identify additional server environment variables, provided by Shibboleth.
At least a few of them should have a name starting with "Shib-". Additionally some other variables might be set by the Shibboleth SP.
Very often, the standard variable ``REMOTE_USER`` is set with the Shibboleth user's ID.
When using https://testshib.org/ you will see this user ID again in a variable named ``eppn``. For details refer to your ``shibboleth2.xml`` file.
Other variables might be useful for retrieving metadata like the clear name of the user.

**Take a copy** of this variable list. You will need it in one of the next steps.

If this doesn't work, you very likely have to work on the Shibboleth SP integration. Don't start configuring the shibboleth extension, before this works.

Configuration of the extension
------------------------------

Configuration of the extension happens in to places. First, in the extension manager you may set
some basic parameters. Second, mapping of attributes delivered by Shibboleth to properties of the
TYPO3 user is defined using TypoScript code inside a text file, the “mapping configuration
file”.

.. toctree::
    :maxdepth: 2
    :titlesonly:

    ConfigurationOptions/Index
    MappingConfigurationFile/Index
    Checklists/Index
