Docs Session #1 API
~~~~~~~~~~~~~~~~~~~

Mature projects have large numbers of operations. Cinder has less, for example.
``node.js/packages`` builds JSON files, outputs to a directory, and viewable HTML format.

Anne Demo:

* "People want swagger for making clients".
* "Make swagger generator look like API docs" stylable to ease transtion
* npn --intall. npn --run bootprint (?)
* Swagger migration is incremental

Items pulled from the nova tree at some point.

**Prerequisite - install a node**

``editor.swagger.io`` -  http://editor.swagger.io/#/

Walkthrough: migration
^^^^^^^^^^^^^^^^^^^^^^

#. Save a copy of the ``.wadl`` file to convert

#. Set up a virtual environment.

#. ..


``ls -api`` , ``v3``.

Troubleshooting

In Wadl, parameters described and not mentioned again in the lower parts of the file may
not be caught by swagger on conversion. Swagger is not set up to catch Wadl errors.

Improvements are incremental in this field.

Wiki page to sign up for certain project work.

Keep major additions to a minimum during conversion. A feature freeze to keep this
plan away from moving targets. Please wait.
