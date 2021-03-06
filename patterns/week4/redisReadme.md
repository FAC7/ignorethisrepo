We highly recommend going through [this tutorial](http://try.redis.io/) before reading the below to give you a good handle on Redis terminology and syntax. Takes roughly 30 mins.

## When to use Redis?

- Caching - because of its speed. Redis can store huge string sizes and can store any content you need to serve in your app; from simple components to entire pages

- List online people in a chat application the list of people/devices that are connected changes frequently (as people join/leave).

- If you have enough time to think about your DB design

- Sessions in your app (which require a DB/io read on every request but don't contain content) should be checked/set as quickly as possible

- If you need really high performance. Beating the performance Redis provides is nearly impossible

## Who uses Redis?

- Instagram uses Redis heavily to run their main feed, activity feed and session store

- Github – Github is using Redis for exception handling and queue management.

- Stack Overflow uses Redis as a caching layer for their entire network.
 
- Pinterest is a heavy user of Redis. They use it for their follower model, which is their graph of who is following whom.

- Twitter makes heavy use of Redis, and has open-sourced some of the projects they built internally to take advantage of Redis.

- Tumblr uses Redis to power dashboard notifications for their tens of millions of users.


##Guide to Installing Redis.

Installing Redis has two dependencies, a working GCC compiler and libc as Redis is written in C.

### Linux/Mac

Pointing to the correct directory in your terminal for your project. Here are the commands to be entered in command line for getting the latest version of Redis. Full instructions can be found on Redis website.
[click here](http://redis.io/topics/quickstart)

```bash
wget http://download.redis.io/redis-stable.tar.gz
tar xvzf redis-stable.tar.gz
cd redis-stable
make
```

### Windows/ Virtual box

If you are using windows or a virtual box creating a development environment you may wish to use Vagrant [click here ](https://github.com/docdis/learn-redis) for instructions.

### Which Node Modules ?  

There are a number of npm modules you can install to use with Redis.
Two recommended node modules are:  

https://www.npmjs.com/package/redis.

https://github.com/redis/hiredis-node. (hiredis-node is a Javascript wrapper which allows us to use Javascript syntax on Redis, even though Redis is written in C)

The commands needed to install both modules are : 

```npm install redis hiredis --save```

### Check if Redis is working

External programs talk to Redis using a [TCP](http://searchnetworking.techtarget.com/definition/TCP) socket and a Redis specific protocol. This protocol is implemented in the Redis client libraries for the different programming languages. However to make hacking with Redis simpler Redis provides a command line utility that can be used to send commands to Redis. This program is called redis-cli.
The first thing to do in order to check if Redis is working properly is sending a PING command using redis-cli (Note you need to open a new terminal window for this and the redis needs to be running ```redis-server```).


```$ redis-cli ping
PONG```

Congratulations you have installed Redis!!!

##Using Redis with Node.js

1. Create a javascript file eg. basic.js  

2. In the basic.js file:
 - require redis
 - create client
 - set your key-pair value to the client (note the use of redis command **'set'**)  

 #####In this example "Username" is the key and "Tom" is the value of that key.

 - call the key-pair value using the **'get'** method on client. The value of the key is going to be represented as 'reply'.

 ```javascript
 var redis  = require("redis");
 var client = redis.createClient();

 client.set("Username", "Tom", redis.print);

 client.get("Username", function(err, reply) {
    // reply is null when the key is missing
    console.log('Hello ' + reply);
 });          
 ```

3. Save the file and start the server **in a separate terminal tab**:  ```redis-server```

4. Run the file in the terminal: ```node basic.js```
   
For further examples of Node syntax for using Redis take a look a this [tutorial](http://www.sitepoint.com/using-redis-node-js/)

![console.log](https://files.gitter.im/Jbarget/Tbs1/Screen-Shot-2015-10-05-at-16.29.11.png)


## Exporting the database

If you need to export your current database or use an existing database with your server we recommend following [this tutorial](http://redis4you.com/articles.php?id=005&name=Seamless+migration+from+one+Redis+server+to+another) 

## Meet the Redis team!

Interested in meeting the brains behind Redis? and talking all things Redis?
RSVP to these two events!

[2nd Annual Redis Developer Day](https://www.eventbrite.com/e/2nd-annual-redis-developer-day-tickets-18073905538)

[2nd Annual Redis unConference](https://www.eventbrite.com/e/2nd-annual-redis-unconference-tickets-18652995612)

## Resources
* [Great guide with Redis commands for Node](http://www.sitepoint.com/using-redis-node-js/)
* [Tutorial on Redis](https://github.com/docdis/learn-redis)
* [Redis's quickstart guide with latest version of Redis](http://redis.io/topics/quickstart)
* [An example of using Redis on Github](https://github.com/nelsonic/hits)
* [Redis data types](http://redis.io/topics/data-types)
* [Intro to Redis Commands](http://try.redis.io/)
* [Learn Vagrant to setup developer environment](https://github.com/dwyl/learn-vagrant)
* [npm modules](https://www.npmjs.com/package/redis)
* [Definition of TCP.](http://searchnetworking.techtarget.com/definition/TCP)

**Vote for us, for RMOTW**

![](https://media.giphy.com/media/MhHXeM4SpKrpC/giphy.gif)
