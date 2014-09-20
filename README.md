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

Download Drupal Coder module & create symlink to it in PHP_Codesniffer standards
```
git clone --branch 7.x-2.x http://git.drupal.org/project/coder.git
ln -s ~/coder/coder_sniffer/Drupal/ ~/.composer/vendor/squizlabs/php_codesniffer/CodeSniffer/Standards/Drupal
```

## Import the Jenkins Job

```java -jar jenkins-cli.jar -s http://JENKINS_URL:8080 create-job JOB_NAME < DrupalCommitAnalytics.xml```
```mkdir /var/lib/jenkins/workspace/JOB_NAME/build```
