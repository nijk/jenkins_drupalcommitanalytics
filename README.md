# Jenkins job for Analysing Drupal Commits

## Pre-requisite external dependencies

**Install these dependencies before beginning the installation process**

* [Jenkins](http://jenkins-ci.org/)
  * [Git plugin](https://wiki.jenkins-ci.org/display/JENKINS/Git+Plugin)
  * [Checkstyle plugin](https://wiki.jenkins-ci.org/display/JENKINS/Checkstyle+Plugin)
  * [DRY plugin](https://wiki.jenkins-ci.org/display/JENKINS/DRY+Plugin)
  * [Plot plugin](https://wiki.jenkins-ci.org/display/JENKINS/Plot+Plugin)
  * [PMD plugin](https://wiki.jenkins-ci.org/display/JENKINS/PMD+Plugin)
  * [Analysis collector plugin](https://wiki.jenkins-ci.org/display/JENKINS/Analysis+Collector+Plugin)

* [Jenkins CLI](http://localhost/cli)
* PHP 5.3 +
* PHP XML
* PHP Process
* [Composer](https://getcomposer.org)
* [Drush Drake](https://www.drupal.org/project/drush_drake)

## Installation

### Setup
1. Copy the composer.json file to ~/.composer so that the composer packages can be installed globally for the user.

2. Run the install process
```
cd ~/.composer
cp .composer .composer-backup
composer global install 
```

3. Configure system to recognise where Drush lives:
```
ln -s /path/to/drush/drush /usr/bin/drush
```

### Drupal Coding Standards
Download Drupal Coder module & create symlink to it in PHP_Codesniffer standards
```
git clone --branch 7.x-2.x http://git.drupal.org/project/coder.git
```
```
ln -s ~/coder/coder_sniffer/Drupal/ ~/.composer/vendor/squizlabs/php_codesniffer/CodeSniffer/Standards/Drupal
```

### Import the Jenkins Job
Import the Jenkins job from the XML template
```
java -jar jenkins-cli.jar -s http://JENKINS_URL:8080 create-job JOB_NAME < DrupalCommitAnalytics.xml
```
```
mkdir /var/lib/jenkins/workspace/JOB_NAME/build
```

### Install Drake
1. Install [Drush Drake](https://www.drupal.org/project/drush_drake)
```
drush dl drush_drake
```
2. Install [Drake CI]()
```
cd /var/lib/jenkins/workspace/JOB_NAME
git clone https://github.com/reload/drake_ci
```

## Issues encountered
1. Jenkins doesn't seem to run .bashrc when it executes jobs, as a result I found that it was necessary to set $PATH vars in jenkins
2. This Jenkins install doesn't seem to like generating images, I followed [these instructions](https://wiki.jenkins-ci.org/display/JENKINS/Jenkins+got+java.awt.headless+problem) and restarted jenkins 
