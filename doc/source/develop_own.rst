Develop own BalderHub project
*****************************

.. note::
    You can also use a BalderHub project internally within your team or organization. There's no need to publish it
    publicly if you prefer to keep it private.

    This flexibility allows you to leverage the framework's features for your own testing needs without sharing it on
    the hub.

The simplest way to create a BalderHub project is by creating it out of a template. We've created
`a own GitHub repository <https://github.com/balder-dev/template-balderhub>`_ that automatically creates a ready to
publish BalderHub project for your specific topic.

The simplest way to create a BalderHub project is by starting from a template. We've created
`a GitHub repository <https://github.com/balder-dev/template-balderhub>` that automatically sets up a ready-to-publish
BalderHub project tailored to your specific topic.

Create your project
===================

We recommend using [cookiecutter](https://github.com/cookiecutter/cookiecutter) to automatically fill in all the
relevant custom fields in the BalderHub project template.

You can install it with pip:

.. code-block:: shell

    $ pip install cookiecutter

With cookiecutter installed, you can create a new project from this template by running one of the following commands:

**For Git Checkout over SSH:**

.. code-block:: shell

    $ python -m cookiecutter git@github.com:balder-dev/template-balderhub.git


**Or for Git Checkout over HTTPS:**

.. code-block:: shell

    $ python -m cookiecutter https://github.com/balder-dev/template-balderhub.git

.. note::

    This command will start Cookiecutter, which creates a new project directory based on the values you specify. Even
    though it uses Git for the checkout process, it will not create a new Git repository for you.

When you run Cookiecutter, it will prompt you with a series of questions to customize your project:

.. code-block:: shell

    $ cookiecutter git@github.com:balder-dev/template-balderhub.git
      [1/10] project_name (Template): FileOps
      [2/10] project_full_name (BalderHub FileOps):
      [3/10] project_slug (fileops):
      [4/10] project_full_slug (balderhub-fileops):
      [5/10] project_decr_short (BalderHub Project that can be used as Template): BalderHub Project that provides features and scenarios to test file operations
      [6/10] project_decr_long (This should be a description of the project, about 1-2 sentences long, which briefly and concisely summarizes what it is about.):
      [7/10] author (Anonymous): Balder Developers
      [8/10] url_documentation (https://hub.balder.dev/projects/fileops):
      [9/10] url_source (https://github.com/balder-dev/balderhub-fileops/):
      [10/10] url_issues (https://github.com/balder-dev/balderhub-fileops/issues):


Your new project
================

As soon as Cookiecutter finishes, it creates a new directory named after the ``project_full_slug`` you provided. Based
on the used data from above, the directory structure might look something like:

.. code-block:: none


.. note::
    When adding new subdirectories, don't forget to add them to the ``setup.cfg`` file.

.. note::
    Please be aware that you need to add your objects to the documentation manually. The template automatically
    creates some ``.. TODO`` flags for you to guide this process.

That's it! You can now start developing features, scenarios, and/or setups.
