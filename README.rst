Reloadr
=======

Python hot code reloading tool.

``pip install reloadr``

Usage
=====

You can simply decorate your functions / classes with ``@autoreload`` and
you are ready to go.

.. code:: python

    from reloadr import autoreload

    @autoreload
    def do_something(a, b):
        return a + b

    @autoreload
    class SomeThing:
        def do_stuff(self):
            pass

Advanced usage
==============

To reload the code manually, you can use of the following:

.. code:: Python

    from reloadr import reloadr

    @reloadr
    class SomeThing:
        def do_stuff(self):
            pass

    # Manual reload
    SomeThing._reload()

    # Automatic reload using filesystem notifications
    SomeThing._start_watch_reload()

    # Automatic reload in a thread every 1 second
    SomeThing._start_timer_reload(1)

Examples
========

Launch an example (they each contain an infinite loop), then change the
source code of the decorated class or function.

``git clone https://github.com/hoh/reloadr.git``

``python examples/01_manual_reload.py``

How it works
============

Instead of importing your source file again, which can lead to undesired side
effects, Reloadr fetches the new code of your function within the Python source
file, and executes that code in the environment of your already loaded module.

This allows it to reload code that is followed by blocking instructions such
as the infinite loops you can find in the examples.

To achieve this, Reloadr relies on  `RedBaron
<https://github.com/psycojoker/redbaron/>`_ , an great tool for manipulating
Python source code.

Future plans
============

This project is still in its early stages. All ideas for improvement are welcome.
