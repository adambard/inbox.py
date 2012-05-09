Inbox.py: SMTP Server for Humans
================================

This is simplest SMTP server you'll ever see. It's asynchronous. 

One instance should handle over one thousand emails per second, thanks to Gevent.


Usage
-----

Give your app an inbox easily::

    from inbox import Inbox

    inbox = Inbox()

    @inbox.collate
    def handle(to, sender, body):
        ...

    # Bind directly.
    inbox.serve(address='0.0.0.0', port=4467)

The handler accepts 3 arguments:

* **to**, a list of email addresses the email was sent to
* **sender**, the "from" email address, as a string
* **body**, the body of the email, including headers, as a string.

You can also defer to the commandline::

    if __name__ == '__main__':
        inbox.dispatch()

::

    $ dasinbox.py 0.0.0.0 4467
    [2012-04-28 07:31] INFO: inbox: Starting SMTP server at 0.0.0.0:4467


Installation
------------

Installing Inbox.py is simple::

    $ pip install inbox