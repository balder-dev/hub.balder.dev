What Is A BalderHub Package
***************************

BalderHub packages are normal Python packages that can easily be included in your specific project. This allows you to
reuse scenario and feature implementations from people all around the world. You only need to provide your custom
implementations that are specific to your device, without rewriting the general test logic.

The main idea behind BalderHub packages is that you can access a wide range of different tests that clever minds have
already thought about. You simply need to import their features and/or scenarios and get started.

Different mock functions, helper devices, or complete testable implementations of remote devices (for example, a
DHCP server for DHCP-client tests) are often already provided in these BalderHub projects. This helps you and your team
develop tests a lot faster.

Example
=======

If you want to write web tests, for example, you can simply install the package ``balderhub-html``. This package allows
you to start creating web tests right away. For instance, you can use the ``balderhub.html.scenario_features.HtmlPage``
class and import the provided HTML elements like this: ``import balderhub.html.lib.utils.components as html``.

.. code-block:: python

    # file `lib/pages.py`

    from balderhub.html.lib.utils import Selector
    import balderhub.html.lib.utils.components as html
    import balderhub.html.lib.scenario_features

    class MyWebsiteMain(balderhub.html.lib.scenario_features.HtmlPage):

        @property
        def span_state(self):
            return html.HtmlSpanElement.by_selector(self.driver, Selector.by_class('state'))

        @property
        def btn_start(self):
            return html.HtmlButtonElement.by_selector(self.driver, Selector.by_id('btnStart'))


And you can write a test for it:

.. code-block:: python

    # file `scenarios/scenario_check_start_button.py`

    import balder
    from lib.pages import MyWebsiteMain

    class ScenarioCheckStartButton(balder.Scenario):

        class Browser(balder.Device):
            page = MyWebsiteMain()

        def test_check_button(self):
            assert self.Browser.page.span_state.text == 'idle'
            self.Browser.page.btn_start.wait_to_be_clickable_for(3).click()
            assert self.Browser.page.span_state.text == 'started'

You want to run it with Selenium? Install it with ``pip install balderhub-selenium`` and just use it in your setup:
If you want to run your tests using Selenium, simply install the package with ``pip install balderhub-selenium``. Then,
you can easily integrate it into your setup. For example, you might define a setup class that uses Selenium as the
driver for the Browser device:

.. code-block:: python

    # file `setups/setup_office.py`

    import balder
    from lib.pages import MyWebsiteMain

    from balderhub.selenium.lib.setup_features import SeleniumChromeWebdriverFeature

    class SetupOffice(balder.Setup):

        class Webserver(balder.Device):
            _my_webpage = MyWebPageFeature()

        class Browser(balder.Device):
            selenium = SeleniumChromeWebdriverFeature()
            page = MyWebsiteMain()


If you don't want to use Selenium as the controlling tool, you can simply replace it with another package that
implements the interface of `balderhub-guicontrol <https://hub.balder.dev/projects/guicontrol>`_.

All you need to do is swap out the ``SeleniumChromeFeature`` with the GUI control feature of your choice, and you'll be
able to run your tests with it seamlessly.

Use a ready-to-use Scenario
---------------------------

You want to test login process? No need to write any test by your self, just provide some specific feature bindings and
the ``balderhub-auth`` package will do the rest for you:

If you want to test a login process, there's no need to write any tests yourself. Simply provide some specific feature
bindings, and the ``balderhub-auth`` package will handle the rest for you. This package includes pre-built scenarios for
common authentication flows, making it quick and straightforward to integrate into your Balder setup.

You can install it with ``pip install balderhub-auth`` and provide the implementation as mentioned in
`their documentation <https://hub.balder.dev/projects/auth>`_:

.. code-block:: python

    # file `lib/pages.py`

    import balderhub.auth.contrib.html.pages
    from balderhub.html.lib.utils import Selector
    from balderhub.url.lib.utils import Url
    import balderhub.html.lib.utils.components as html


    class LoginPage(balderhub.auth.contrib.html.pages.LoginPage):

        url = Url('https://example.com')

        # Overwrite abstract property
        @property
        def input_username(self):
            return html.inputs.HtmlTextInput.by_selector(self.driver, Selector.by_name('user'))

        @property
        def input_password(self):
            return html.inputs.HtmlPasswordInput.by_selector(self.driver, Selector.by_name('user'))

        @property
        def btn_login(self):
            return html.HtmlButtonElement.by_selector(self.driver, Selector.by_id('submit-button'))



And add it to our setup:

.. code-block:: python

    # file `setups/setup_office.py`

    import balder
    import balderhub.auth.lib.scenario_features.role
    from lib.pages import MyWebsiteMain, LoginPage

    class UserConfig(balderhub.auth.lib.scenario_features.role.UserRoleFeature):

        username = 'admin'
        password = 'secret'

    class SetupOffice(balder.Setup):

        class Webserver(balder.Device):
            user = UserConfig()

        class Browser(balder.Device):
            ...
            page_login = LoginPage()

Finally import the relevant scenario class in a ``scenario_*.py`` file:


.. code-block:: python

    # file `scenarios/balderhub/scenario_balderhub.py`

    from balderhub.auth.scenarios import ScenarioSimpleLogin

Run Balder and the test provided by the class ``ScenarioSimpleLogin`` of ``balderhub-auth`` will be executed for you!
