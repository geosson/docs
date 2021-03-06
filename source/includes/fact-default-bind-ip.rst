Starting in MongoDB 3.6, MongoDB binaries, :program:`mongod` and
:program:`mongos`, bind to localhost by default.

Previously, starting from MongoDB 2.6, only the binaries from the
official MongoDB RPM (Red Hat, CentOS, Fedora Linux, and derivatives)
and DEB (Debian, Ubuntu, and derivatives) packages bind to localhost by
default.

When bound only to the localhost, these MongoDB 3.6 binaries can only
accept connections from clients (including the :program:`mongo` shell,
other :program:`mongod` instances and :program:`mongos` instances) that
are running on the same machine. Remote clients cannot connect to the
binaries bound only to localhost.

To override and bind to other ip addresses, you can use the
:setting:`net.bindIp` configuration file setting or the ``--bind_ip``
command-line option to specify a list of ip addresses

For example, the following :program:`mongod` instance binds to both the
localhost and another ip address:

.. code-block:: sh

   mongod --bind_ip localhost,198.51.100.1

Remote clients must specify the ip address ``198.51.100.1`` or the
associated hostname in order to connect to this instances:

.. code-block:: sh

   mongo --host 198.51.100.1

   mongo --host My-Example-Associated-Hostname

