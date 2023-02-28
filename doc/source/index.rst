.. BalderHub Entry Page documentation master file, created by
   sphinx-quickstart on Sun Feb 26 20:05:20 2023.
   You can adapt this file completely to your liking, but it should at least
   contain the root `toctree` directive.

BalderHub
=========

Balder grand vision is to create an open-source, share space for testing-projects. This page gives an overview over all
BalderHub packages that are contained in the `balder-dev GitHub group <https://github.com/balder-dev>`_. We hope this
page makes it easier for developers to find and contribute to such open-source projects.

.. note::

   Balder is a very young project. Unfortunately, this also means that we do not have so many BalderHub projects at the
   moment.

   We need your help here. There are a lot of people in this world, that are experts in the thing they are doing and
   exactly these experts we need here.

   Do you know one area really well? Do you like the concept of balder? Think about to initiate an own
   BalderHub project. Take a look into our `Balder GitHub Group <https://github.com/balder-dev>`_ and feel free to
   contribute to an existing project or create your own one. If you are not secure if your subject already exist or
   if you are searching for some colleagues to develop a BalderHub project within a group, fell free to
   `create an issue <https://github.com/balder-dev/hub.balder.dev>`_ or
   `start a new discussion <https://github.com/balder-dev/hub.balder.dev/discussions>`_.

Existing projects
-----------------

.. toctree::
   :maxdepth: 2

   balderhub-snmpagent <https://hub.balder.dev/projects/snmpagent>

What are BalderHub packages?
----------------------------

BalderHub packages are normal python packages, that can easily be included into your specific project. This allows
you to reuse scenario and feature implementation from people all around the world. You only need to provide your custom
implementation that really depends on your device, but not the general test logic.


The main idea of BalderHub packages is that you can access a wide range of different tests where a lot of clever minds
has already think about. You simply need to import their scenarios, add the specific setup-device feature code for your
device and go for it. Different mock functions, helper devices or
complete testable implementations of remote devices (for example a dhcp server for dhcp-client tests) are often already
provided in these BalderHub project. This helps you and your team to develop test a lot faster.