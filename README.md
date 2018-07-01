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

