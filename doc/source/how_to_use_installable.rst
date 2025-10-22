How To Use An Installable Package
*********************************

If you want to use an existing BalderHub package in your project, you simply need to install it with pip:

.. code-block:: shell

    $ pip install balderhub-<the package>

Select & Activate Scenarios
===========================

After you have installed it, you can easily import the scenarios that you want to activate.

To do this, import your scenario according to the documentation of the BalderHub package, inside a Python module whose
filename starts with ``scenario_*.py`` (for example, ``scenario_my_test.py``). This naming convention is required
because Balder only collects files that match this pattern when searching for scenarios.

For example, if you want to use some scenarios from the
`balderhub-snmpagent package <https://hub.balder.dev/projects/snmpagent>`_, you can do the following:

.. code-block:: python

    # file `scenario_balderhub.py``
    from balderhub.snmpagent.scenarios.base import ScenarioMibSysDescr, ScenarioMibSysObjectId, ScenarioMibSysUpTime

That's all. With this, you have added these test scenarios to your test project and Balder will collect them.


Implement necessary features
============================

Some projects are already shipped with ready-to-use features on setup-level that can easily be used. Just import them
and instantiate them in your setup devices.

Independent if you are using some shipped setup-features, you often have to provide own config features, which hold
information like the IP address of you device or something like that. Simply overwrite them and provide
an implementation for all abstract methods or properties. You can find more information about them in the specific
documentation of your selected BalderHub project.

Some BalderHub projects are already shipped with ready-to-use features at the setup level that you can easily
incorporate. Simply import them and instantiate them in your setup devices.

Regardless of whether you are using these shipped setup features, you often need to provide your own config features.
These hold specific information, such as the IP address of your device or similar details. Just override them and
provide implementations for all abstract methods or properties. You can find more details about them in the EXAMPLE
SECTION of the specific documentation of your selected BalderHub project.

Add necessary features to your setup devices
============================================

After you have overridden all the necessary features, you simply need to add them to your setup features.