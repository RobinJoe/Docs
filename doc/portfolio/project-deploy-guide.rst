Writing Sample 
==============

Original Content available on the `OpenStack Documentation website <https://docs.openstack.org/doc-contrib-guide/project-deploy-guide.html>`_.


*The following content is preceded by another procedure. See the above link to explore the complete background*

*In summary, The procedure involves configuring and deploying a specific deployment guide for each project.* 

After these changes merge, you can set up the jobs for building in the
OpenStack Infra ``project-config`` repository:

#. Clone the project-config repo:

   .. code-block:: console

      $ git clone https://git.openstack.org/openstack-infra/project-config

#. In ``jenkins/jobs/projects.yaml``, add ``deploy-guide-jobs`` within the
   entry for your project:

   .. code-block:: yaml

      - project:
        name: <project-name>

        jobs:
        ...
         - deploy-guide-jobs:
             service: <service-name>

   ``project-name`` and ``service-name`` are the project name, and the
   specific serivce name. One example is orchestration for heat.

   This defines the jobs using the JJB ``deploy-guide-jobs`` job-template.

#. In ``zuul/layout.yaml``, locate the entry for your project and add the
   ``deploy-guide-jobs`` template:

   .. code-block:: yaml

      - name: openstack/<project-name>
        template:
          - name: deploy-guide-jobs

   This schedules the Deploy Guide jobs.

#. Commit the changes to the infra repository for review.

