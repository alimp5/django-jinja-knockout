.. _3bs.sh: https://github.com/Dmitri-Sintsov/djk-sample/blob/master/3bs.sh
.. _4bs.sh: https://github.com/Dmitri-Sintsov/djk-sample/blob/master/4bs.sh
.. _Bootstrap 3: https://getbootstrap.com/docs/3.3/
.. _Bootstrap 4: https://getbootstrap.com/docs/4.1/
.. _djk-bootstrap3: https://github.com/Dmitri-Sintsov/djk-bootstrap3
.. _djk-bootstrap4: https://github.com/Dmitri-Sintsov/djk-bootstrap4
.. _requirements-bs3.txt: https://github.com/Dmitri-Sintsov/djk-sample/blob/master/requirements-bs3.txt
.. _requirements-bs4.txt: https://github.com/Dmitri-Sintsov/djk-sample/blob/master/requirements-bs4.txt


======
djk_ui
======

Since v0.8.0, django-jinja-knockout supports both `Bootstrap 3`_ and `Bootstrap 4`_ via the ``djk_ui`` Django
application module.

``djk_ui`` module is installed from `djk-bootstrap3`_ / `djk-bootstrap4`_ packages, respectively. This means that
`djk-bootstrap3`_ and `djk-bootstrap4`_ packages are mutually exclusive and only one has to be installed in the project
virtualenv at the same time. Unfortunately pip does not support requirements.txt files with deinstallation directives.
Thus one has to use pip with separate `requirements-bs3.txt`_ / `requirements-bs4.txt`_ files, to install the current
stable version, or to copy and then run `3bs.sh`_ / `4bs.sh`_ shell scripts, to switch between current master (possibly
unstable) versions of ``djk_ui``. Usually most of projects does not require changing Bootstrap version on the fly, so
that's not much of problem.

.. _djk_ui_conf:

conf.py
-------
Contains the default ``layout_classes`` values, for example for Bootstrap 4 v0.8.0 that is::

    LAYOUT_CLASSES = {
        '': {
            'label': 'col-md-3',
            'field': 'col-md-7',
        },
        'display': {
            'label': 'w-25 table-light',
            'field': 'w-100 table-default',
        },
    }

where '' key specifies the layout classes of editable model forms, 'display' key specifies the layout classes of the
display-only model forms.

These default values can be overriden via the project `settings` module ``LAYOUT_CLASSES`` variable. See also
:ref:`forms_opts` for more info how layout classes are applied to form / formset renderers; see
:ref:`macros_layout_classes` how layout classes are used in form / formset macros.

Customization
-------------
This module implements both server-side (Python) and client-side (Javascript) parts of the code that differs between
`Bootstrap 3`_ and `Bootstrap 4`_. While it's possible to implement much larger ``djk_ui`` wrappers for more generic UIs,
currently I do not have enough of time / resources for that.