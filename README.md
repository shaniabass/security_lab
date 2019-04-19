# security_lab
CS132 Spring 2019 Security Lab

## Phase 2: Configuration
Before reading this README, please make sure you've completed the instructions on Prelab 2 Phase 1. As a reminder, that phase introduced you to the VM where your application will be running on. It was also during that phase where you've forked this directory.

This part is very important, and you should do this portion of the lab carefully to ensure that your server will be running smoothly (until some other group attacks it of course!).

In particular, there are two files that you'll want to configure: _config.js_ and _./db/create.sql_. At this point, however, if you have not yet received an email from us about your _username_, _password_, _database_, and _port #_, then you should **stop** and make sure you've obtained these credentials. If you know these credentials, great! Let's start.

### Saving your Settings
In the event that your application has been hacked, you'll have to restart your application from scratch. If you don't want to go through the entire configuration process again, push all these changes to the forked repository. Then, whenever you've been attacked, restarting the application is a matter of just pulling from your git repo, and re-running the create.sql script.

### Running Your Application
1. Navigate back to the application project root.
2. Run
> npm install

   You might encounter some error messages by node, but for now let's ignore them. Check your node_modules directory, and if there are the following modules, you're set:

   * any-db
   * any-db-mysql  
   * body-parser  
   * consolidate
   * express  
   * express-session  
   * marked
   * morgan
   * serve-favicon
   * swig
   * underscore
3. Run
> node server.js

> chromium &

4. Navigate to 'localhost:PORT' where PORT is the port number you've configured previously.
