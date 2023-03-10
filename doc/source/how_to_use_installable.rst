How To Use An Installable Package
*********************************

If you want to use an already existing package in your project you just need to install it with pip:

.. code-block::

    pip install balderhub-<the package>

Select & Activate Scenarios
===========================

After you have installed it you can easily import the scenarios that you want to activate.

For this import your scenario according to the documentation of the BalderHub package inside a python module that starts
with ``scenario_*.py``. This is needed, because Balder only collects files that have this name while searching for
scenarios.

For example, if you want to use some scenarios from the
`balderhub-snmpagent package <https://hub.balder.dev/projects/snmpagent>`_ you can do the following:

.. code-block:: python

    # file `scenario_balderhub.py``
    from balderhub.snmpagent.scenarios.base import ScenarioMibSysDescr, ScenarioMibSysObjectId, ScenarioMibSysUpTime

That's all. With this you added these scenarios to your project.

Implement necessary features
============================

Some projects are already shipped with ready-to-use features on setup-level that can easily be used. Just import them
and instantiate them in your setup devices.

Independent if you are using some shipped setup-features, you often have to provide own config features, which hold
information like the IP address of you device or something like that. Simply overwrite them and provide
an implementation for all abstract methods or properties. You can find more information about them in the specific
documentation of your selected BalderHub project.

Add necessary features to your setup devices
============================================

After you have overwritten all necessary features, you just need to add them to your setup features.