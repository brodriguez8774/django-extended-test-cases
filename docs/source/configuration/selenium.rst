Selenium Setting Configuration
******************************

The following
`Django settings <https://docs.djangoproject.com/en/dev/topics/settings/>`_
allow configuration of the **ExpandedTestCases** package, regarding settings
for selenium handling when using :doc:`../test_cases/live_server_test_case`
classes.

All of these settings are optional, and will fall back to a default value if
not defined.


General Selenium Settings
=========================

SELENIUM_BROWSER
----------------

When using the :doc:`../test_cases/live_server_test_case` classes
for `Selenium <https://www.selenium.dev/>`_ tests,
this setting specifies which browser to use.

Currently, supported test browsers are as follows:
 * chrome
 * chromium
 * firefox


:Type: ``string``
:Default: ``chrome``

**Example:**

.. code::

    DJANGO_EXPANDED_TESTCASES_SELENIUM_BROWSER = 'firefox'


SELENIUM_HEADLESS
-----------------

This controls if selenium tests should run in "headless" mode or not.

The default (False) is to visually show browser while running tests.
"Headless" (True) will skip visually rendering the browser while running tests.

Headless tends to be good for speed but bad for debugging issues.


:Type: ``bool``
:Default: ``False``

**Example:**

.. code::

    DJANGO_EXPANDED_TESTCASES_SELENIUM_BROWSER = True


SELENIUM_DISABLE_CACHE
----------------------

When True, sets the selenium browser cache to be ignored.

Using the cache can sometimes lead to incorrect/failing tests when running
selenium in a multi-threaded environment.


:Type: ``bool``
:Default: ``False``

**Example:**

.. code::

    DJANGO_EXPANDED_TESTCASES_SELENIUM_DISABLE_CACHE = True


SELENIUM_DEBUG_PORT_START_VALUE
-------------------------------

Indicates the starting debug port, to get around the ``remote-debugging-port``
using the same value for all generated drivers.

Using the same port seems to cause issues with allowing proper switching
between drivers.

To get around this, each driver generated by this package will increment
this port value by one, to guarantee all tests among all files should have
unique ports.


:Type: ``int``
:Default: ``9221``

**Example:**

.. code::

    DJANGO_EXPANDED_TESTCASES_SELENIUM_DEBUG_PORT_START_VALUE = 9221


SELENIUM_WINDOW_POSITIONS
-------------------------

A list of lists, comprised of desired (x, y) window positions to spawn
selenium browsers at.

If not provided, then defaults to however the OS spawns windows in.

Ex: ``[(0, 0), (960, 0)]`` for two window positions in a standard
1920 x 1080 landscape display.


:Type: ``list`` of ``lists``, each inner list in the format of ``int, int``
:Default: ``None``

**Example:**

.. code::

    DJANGO_EXPANDED_TESTCASES_SELENIUM_WINDOW_POSITIONS = ``[(0, 0), (960, 0)]``


SELENIUM_EXTRA_BROWSER_OPTIONS
------------------------------

Extra options to pass into browser.
Should be provided as a list of values.


:Type: ``list``
:Default: ``None``

**Example:**

.. code::

    DJANGO_EXPANDED_TESTCASES_SELENIUM_EXTRA_BROWSER_OPTIONS = [
        'value_1',
        'value_2'
    )


SELENIUM_DRIVER_LEVEL
---------------------

Location to auto-create drivers for tests.
Should be either "class" or "method".

The "class" option will create drivers on test class startup, that all test
methods will share.

The "method" option will instead create drivers on each test method instance.


:Type: ``string``
:Default: ``method``
:Options: [``method``, ``class``]

**Example:**

.. code::

    DJANGO_EXPANDED_TESTCASES_SELENIUM_DRIVER_LEVEL = 'class'


Selenium Timeout Settings
=========================

SELENIUM_PAGE_TIMEOUT_DEFAULT
-----------------------------

Number of seconds to wait on selenium page load before giving up.

Refers to the full page itself loading.
As in, getting any page response at all.


:Type: ``int``
:Default: ``30``

**Example:**

.. code::

    DJANGO_EXPANDED_TESTCASES_SELENIUM_PAGE_TIMEOUT_DEFAULT = 30


SELENIUM_IMPLICIT_WAIT_DEFAULT
------------------------------

Number of seconds to wait on selenium page element
(constantly checking for existence) before giving up.

Refers to a specific element loading within a page.
Default of 5 seconds.


:Type: ``int``
:Default: ``5``

**Example:**

.. code::

    DJANGO_EXPANDED_TESTCASES_SELENIUM_IMPLICIT_WAIT_DEFAULT = 30
