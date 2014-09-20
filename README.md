# Jenkins job for Analysing Drupal Commits

## External dependencies

* [Jenkins](http://jenkins-ci.org/)
* [Jenkins CLI](http://yourserver.com/cli)
* PHP 5.3 +
* PHP XML
* PHP Process
* [Composer](https://getcomposer.org)
* [Drush Drake](https://www.drupal.org/project/drush_drake)


## Installation

Copy the composer.json file to ~/.composer so that the composer packages can be installed globally for the user.

Configure system to recognise where Drush lives:
```ln -s /path/to/drush/drush /usr/bin/drush```
