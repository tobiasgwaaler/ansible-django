ansible-django
==============


# TODO:
[ ] Del opp bootstrap i mindre deler slik at f.eks. nginx.conf kan oppdateres uten at databasen settes opp på nytt
[ ] Lag task for å ta backup av "media"
[ ] Lag task for å ta backup av db
[ ] støtte for flere miljøer/instanser på samme server


Nice to have:
[ ] rollback?
[ ] http basic auth-config på qa og test
[ ] Create stronger (ideally random) passwords for users. They can be generated and stored in files on the remote host.
[ ] Disable ssh for postgres-user after setup?
[ ] Disable ssh for root og lag en admin-bruker med sudo-rettigheter (mange av kommandoene må da bruke "sudo: yes" og "--ask-sudo-pass")
[ ] Integrate with Django settings:
      uploaded_files = os.getenv(["DJANGO_UPLOADED_FILES_DIR"])
      static_files = os.getenv(["DJANGO_STATIC_FILES_DIR"])
      database params must be set to 
      os.getenv(["DJANGO_POSTGRES_DB"])
      os.getenv(["DJANGO_POSTGRES_USER"])
      os.getenv(["DJANGO_POSTGRES_PASSWD"])

















An opinionated server setup for running Django applications. 
This script uses Ansible to install some of the most common dependencies for a Django application to a remote server.


## Server requirements ##
- Tested on ubunut 12.04 LTS, but might work on other versions of Ubuntu (as well as other distros using apt).

## Usage ##
Prerequisits:
Ansible-django expects to find the following at the root of your project:
- A folder called "static" where static files are collected to on "collectstatic". Set STATIC_ROOT to point to this directory
- A folder called "media" where uploaded files can be stored. Set MEDIA_ROOT to point to this directory
- STATIC_URL = '/static/'
- MEDIA_URL = '/media/'

NB! To avoid overwriting all your uploaded media files whenever you deploy, make sure the "media" directory is in your .gitignore (and that the .gitignore-file is tracked by git).



- Add ansible-django as a git submodule to your django project:
- git submodule add ssh://git@bitbucket.org/tobiasgw/ansible-django.git
- Add "ansible-django" and ".gitsubmodules" to your .gitignore
- Create "config.yml" with project-specific configurations


