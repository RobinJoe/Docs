Manage projects and users
=========================

Publicly available on the `OpenStack Horizon documentation page <https://docs.openstack.org/horizon/latest/admin/manage-projects-and-users.html>`_.

OpenStack administrators can create projects, and create accounts for new users
using the OpenStack Dasboard. Projects own specific resources in your
OpenStack environment. You can associate users with roles, projects, or both.

Add a new project
~~~~~~~~~~~~~~~~~

#. Log into the OpenStack Dashboard as the Admin user.
#. Click on the `Identity` label on the left column, and click
   ``Projects``.
#. Select the ``Create Project`` push button.
   The `Create Project` window will open.
#. Enter the Project name and description. Leave the `Domain ID`
   field set at *default*.
#. Click ``Create Project``.

.. note::

   Your new project will appear in the list of projects displayed under the
   ``Projects`` page of the dashboard. Projects are listed in
   alphabetical order, and you can check on the **Project ID**, **Domain
   name**, and status of the project in this section.

Delete a project
~~~~~~~~~~~~~~~~

#. Log into the OpenStack Dashboard as the Admin user.
#. Click on the ``Identity`` label on the left column, and click
   ``Projects``.
#. Select the checkbox to the left of the project you would like to delete.
#. Click on the ``Delete Projects`` push button.

Update a project
~~~~~~~~~~~~~~~~

#. Log into the OpenStack Dashboard as the Admin user.
#. Click on the ``Identity`` label on the left column, and click
   ``Projects``.
#. Locate the project you wish to update, and under the ``Actions``
   column click on the drop down arrow next to the ``Manage Members``
   push button. The ``Update Project`` window will open.
#. Update the name of the project, enable the project, or disable the project
   as needed.

Add a new user
~~~~~~~~~~~~~~

#. Log into the OpenStack Dashboard as the Admin user.
#. Click on the ``Identity`` label on the left column, and click
   'Users'.
#. Click ``Create User``.
#. Enter a `Domain Name`, the `Username`, a
   `password` for the new user. Enter an email for the new user,
   and specify which `Primary Project` they belong to. Leave the
   `Domain ID` field set at *default*. You can also enter a
   decription for the new user.
#. Click the ``Create User`` push button.

.. note::

   The new user will then appear in the list of projects displayed under
   the `Users` page of the dashboard. You can check on the
   **User Name**, **User ID**, **Domain name**, and the User status in this
   section.

Delete a new user
~~~~~~~~~~~~~~~~~

#. Log into the OpenStack Dashboard as the Admin user.
#. Click on the `Identity` label on the left column, and click
   ``Users``.
#. Select the checkbox to the left of the user you would like to delete.
#. Click on the `Delete Users` push button.

Update a user
~~~~~~~~~~~~~

#. Log into the OpenStack Dashboard as the Admin user.
#. Click on the `Identity` label on the left column, and click
   ``Users``.
#. Locate the User you would like to update, and select the `Edit`
   push button under the `Actions` column.
#. Adjust the `Domain Name`, `User Name`,
   `Description`, `Email`, and `Primary Project`.

Enable or disable a user
------------------------

#. Log into the OpenStack Dashboard as the Admin user.
#. Click on the `Identity` label on the left column, and click
   ``Users``.
#. Locate the User you would like to update, and select the arrow to the right
   of the ``Edit`` push button. This will open a drop down menu.
#. Select ``Disable User``.

.. note::

   To reactivate a disabled user, select ``Enable User`` under
   the drop down menu.

