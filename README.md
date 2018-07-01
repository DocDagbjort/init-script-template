Linux Mochimo Auto Start/Stop Script
------------------------------------

This script allows the mochimo node to start automatically on boot as a service, and to shut down cleanly if the system is rebooted or shut down.

It's just a fork of 'fhd/init-script-template' with the blank values populated and a couple of compatibility tweaks.

Assumptions
-----------

It assumes you've created a user called 'cpuminer' on your Linux machine and have installed the mochimo software at:

    /home/cpuminer/mochimo/mochi/bin

It also assumes you want to run with the '-s250000' flag set to cause the mochimo listener to spend more time sleeping, and less time listening (with the aim of maximising mining time).

Tested only on Ubuntu 16.04, but should work on any System V compatible Linux distribution.

It also assumes that you've completed the initial start of mochimo and have shut it down cleanly from its monitor (i.e. so that it can be restarted with the 'resume' command).


Installation
------------

Copy the 'mochimo' file to:

    /etc/init.d/

Make any changes you require to the 'dir', 'cmd' and 'user' fields (in case you're running mochimo as a different user, or from a different path, or want to change any of the flags).

Ensure the file is executable:

    chmod 755 /etc/init.d/mochimo

Then run:

    update-rc.d mochimo defaults


Usage
-----

To start manually:

    service mochimo start

To stop the node:

    service mochimo stop

The 'start' and 'stop' will obviously happen automatically on boot / shutdown of the Linux system.


Watching the logs
-----------------

Output from mochimo will now be logged in:

    /var/log/mochimo.log

So, you can watch the progresso of the node 'live' with:

    tail -f /var/log/mochimo.log





Original readme rrom fhd/init-script-template included below 
------------------------------------------------------------




System V init script template
=============================

A simple template for init scripts that provide the start, stop,
restart and status commands.

Handy for [Node.js](http://nodejs.org) apps and everything
else that runs itself.

Getting started
---------------

Copy _template_ to /etc/init.d and rename it to something
meaningful. Then edit the script and enter that name after _Provides:_
(between _### BEGIN INIT INFO_ and _### END INIT INFO_).

Now set the following three variables in the script:

### dir ###

The working directory of your process.

### cmd ###

The command line to start the process.

### user ###

The user that should execute the command (optional).
If not set, the command will be called as root (via `sudo ...`).

Here's an example for an app called
[algorithms](http://algorithms.ubercode.de):

    dir="/var/apps/algorithms"
    cmd="node server.js"
    user="node"

Script usage
------------

### Start ###

Starts the app.

    /etc/init.d/algorithms start

### Stop ###

Stops the app.

    /etc/init.d/algorithms stop

### Restart ###

Restarts the app.

    /etc/init.d/algorithms restart

### Status ###

Tells you whether the app is running. Exits with _0_ if it is and _1_
otherwise.

    /etc/init.d/algorithms status

Logging
-------

By default, standard output goes to _/var/log/scriptname.log_ and
error output to _/var/log/scriptname.err_. If you're not happy with
that, change the variables `stdout_log` and `stderr_log`.

License
-------

Copyright (C) 2012-2014 Felix H. Dahlke

This is open source software, licensed under the MIT License. See the
file LICENSE for details.
