Getting Elasticsearch Up and Running Locally With Docker
========================================================

.. index:: Docker

The steps below will get you up and running elasticsearch in a local development environment.
All of these commands assume you are in the project root.


Prerequisites
-------------

* Docker; if you don't have it yet, follow the `installation instructions`_;
* Docker Compose; refer to the official documentation for the `installation guide`_.

.. _`installation instructions`: https://docs.docker.com/install/#supported-platforms
.. _`installation guide`: https://docs.docker.com/compose/install/


Build the Stack (currently unnecessary)
---------------------------------------

Currently, the dev stack consists of prebuilt images. In the future,
if custom docker images are added to the compose file, this may be necessary::

    $ docker-compose build --no-cache


Run the Stack
-------------

This brings up Elasticsearch. The first time it is run it might take a while to get started, but subsequent runs will occur quickly.

Open a terminal at the project root and run the following for local development::

    $ docker-compose up

To rebuild the stack after ``docker-compose build --no-cache``, run this first::

    $ docker-compose down

To run the psql shell for postgres::

    $ docker-compose exec db psql "postgresql://pguser:pgpass@localhost/pgdb"


Tips & Tricks
-------------

Activate a Docker Machine
~~~~~~~~~~~~~~~~~~~~~~~~~

This tells our computer that all future commands are specifically for the dev1 machine. Using the ``eval`` command we can switch machines as needed.::

    $ eval "$(docker-machine env dev1)"
