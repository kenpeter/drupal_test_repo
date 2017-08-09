# Intro

How to do the following in Drupal 7 or 8? High level description should be enough.

# Question 1
Create an event content type with:
* Date fields for start/end
* Hero image
* Event details
* The option to select 1 of 5 people as the event contact

# Question 2
Create two 'Selected Events' blocks
* One of the most recent 3 events
* One of three author selectable events

# Keys to meet
* Where this will be created
* How this will be pushed to the cloud environment


# Approach
I setup a drupal 8 instance to test it. It is best for you to login into the site and see the setting.
I also include the answers below.

* Demo site: http://drupaltest.shopshop.space
* Login: http://drupaltest.shopshop.space/user
* username: admin
* password: admin


# Answers to questions

## For question 1
![alt img](https://github.com/kenpeter/drupal_test_repo/raw/master/misc/event_field.png)

* My custom content type is call 'my_event'
* Date fields for start/end. I create the start date and end date fields.
* Hero image. It is a file field.
* Event details. Long text field with summary.
* The option to select 1 of 5 people as the event contact. It is an entity reference to user entity in Drupal.
* I also create the author field, which references use entity. This allows admin quickly assign author to the event.

## How this will be pushed to the cloud environment
* ```drush config-export --destination='/x/y/z'```, this will export all the configurations (fields, views, blocks, core, etc) to path ```/x/y/z```
* Path ```/x/y/z``` has many ```*.yml``` files. They are under version control. We commit changes within ```/x/y/z/*.yml``` and push to bitbucket, e.g.
* In the cloud, we manually pull down those ```*.yml```.
* drush config-import --source='/x/y/z', to import all the configurations.
* We can certainly write some scripts to automate the process. For reading for myself: https://chromatichq.com/blog/drupal-8-deployments-jenkins-github-slack

# Ref
* https://www.linuxbabe.com/linux-server/drupal-8-ubuntu-16-04-nginx-mariadb-php7
* https://drushcommands.com/drush-8x/config/config-import/
