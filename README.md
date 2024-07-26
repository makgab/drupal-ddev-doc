# DRUPAL development modules and themes with ddev



## Homepage and docs:

 - https://www.drupal.org
 - https://www.drupal.org/docs/official_docs/local-development-guide
 - https://ddev.readthedocs.io/en/stable/users/install/ddev-installation/#linux

 - https://www.drupal.org/docs/develop/creating-modules

 - Acquia Drupal Module develpoment course:
   https://www.youtube.com/playlist?list=PLpVC00PAQQxFNDfiXn6LH1gOLllGS3hhl

 - Acquia Drupal Theme development course:
   https://www.youtube.com/playlist?list=PLpVC00PAQQxGw-jupPsnJOmWgE3YE3-AK



## Docker install:

 - https://docs.docker.com/engine/install/fedora/

```
sudo dnf -y install dnf-plugins-core
sudo dnf config-manager --add-repo https://download.docker.com/linux/fedora/docker-ce.repo

sudo dnf install docker-ce docker-ce-cli containerd.io docker-buildx-plugin docker-compose-plugin

# add user to group 'docker'!

sudo systemctl start docker

sudo docker run hello-world
```



## DDEV install:

 - ddev install Fedora Linux:

```
sudo sh -c 'echo ""'
echo '[ddev]
name=ddev
baseurl=https://pkg.ddev.com/yum/
gpgcheck=0
enabled=1' | perl -p -e 's/^ +//' | sudo tee /etc/yum.repos.d/ddev.repo >/dev/null

# Install DDEV
sudo sh -c 'echo ""'
sudo dnf install --refresh ddev

# One-time initialization of mkcert
mkcert -install
```



## Development with ddev:

 - Configure your local development environment to serve your application:
```
mkdir my-site
cd my-site
ddev config --project-type drupal --docroot web

# This will create a new DDEV project configured to host a Drupal application.
# DDEV will store the generated configuration in a new .ddev subdirectory.
# Project name will be the same as the parent folder (my-site), define it with --project-name solrcloud.

ddev start
```

 - Create a new Drupal application:
```
ddev composer create drupal/recommended-project -y

# composer create-project drupal/recommended-project
```

 - Install Drupal:
```
ddev composer require drush/drush

ddev drush site:install -y          # --account-name=myusername --account-pass=my-password
```

 - Login:
```
ddev launch

ddev drush user:login

# If necessary, execute 'ddev describe' to view the URL of your site. Copy and paste that URL into your web browser to visit it.
```







:)

