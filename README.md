ansible-django
==============

An opinionated server setup for running Django applications. 
This script uses Ansible to install some of the most common dependencies for a Django application to a remote server.

Developed and tested on Ubuntu 12.04 LTS, but might work on other versions of Ubuntu (as well as other distros using apt).

## Security issues ##
At this point using ansible-django to setup your server(s) will result in an insecure server:
- SSH-access as ``root`` and ``postgres`` is permitted.

## Usage ##
Ansible-django expects to find the following at the root of your django project:
- A folder called "static" where static files are collected to on "collectstatic". Set ``STATIC_ROOT`` in your django settings to point to this directory.
- A folder called "media" where uploaded files can be stored. Set ``MEDIA_ROOT`` in your django settings to point to this directory.
Your django settings file should also include ``STATIC_URL = '/static/'``
and ``MEDIA_URL = '/media/'``

NB! To avoid overwriting all your uploaded media files whenever you deploy, make sure the "media" directory is in your .gitignore (and that the .gitignore-file is tracked by git).

To start using ansible-django you can either fork this repo, or add it as a submodule to a django project:

1. ``git submodule add git@github.com:tobiasgwaaler/ansible-django.git`` or ``git clone git@github.com:tobiasgwaaler/ansible-django.git``
2. Add ``ansible-django`` and ``.gitsubmodules`` to the ``.gitignore`` in the parent folder
3. Create ``config.yml`` and ``hosts`` with project-specific configurations in the parent folder
 






