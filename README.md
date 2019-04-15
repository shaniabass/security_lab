#Notes For Lab Handin

 #Lab 8
 
 ##ATTACK 1:
 
 Attacked http://ec2-52-90-199-138.compute-1.amazonaws.com:8080 - Yusuf, John, Brian by changing username
 
 Oops.. 
 Error: ER_PARSE_ERROR: You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near 'DROP TABLE users;"'' at line 1
 
 Attack Method: "'; DROP TABLE users;"
 
 Resolution:
 
 Preventing server side javascript injection attacks should be done by using parameters instead of constructing strings. For example, the query should be set up in this format instead : 

db.query("SELECT * FROM User WHERE userId=?", [req.session.userId], function(error, data) { 
         // Do stuff with data 
});
 
 
 ##ATTACK 2:
 
 Attacked: http://ec2-18-219-228-255.us-east-2.compute.amazonaws.com:8080/login
 
 Attack: eval(res.end(require('fs').readdirSync('.').toString()))
 Oops.. 
 
 Error: ER_PARSE_ERROR: You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near 'fs').readdirSync('.').toString()))'' at line 1
 
 Resolution: Using JSON.parse() instead of eval().
 
 ##ATTACK 3:
 http://ec2-18-208-136-252.compute-1.amazonaws.com:8080/login
 
 Attack: setTimeout(while(1)

 Resolution: Using JSON.parse() instead of eval().










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
