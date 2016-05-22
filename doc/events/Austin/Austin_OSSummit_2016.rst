Openstack Austin Summit 2016
============================

The OpenStack Summit and Design Summit returned to Austin in 2016 for
presentations of what the community has learned during the Mitaka
release cycle, and to begin planning for the Newton release.

I have separated out my report by Day. Later Days in this write-up capture
The valuable design summit sessions. Networking with developers seeking
documentation insight was what made these sessions valuable from
my point of view.

Session #1. Liberty Upgrade - what worked for the Operations Guide
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

.. note::

   These are notes that I have edited from the original version.
   Many comments are opinions or thoughts expressed by speakers
   in the rooms, presented here anonymously. These views are not
   my own. They are an open record of what was discussed.

Documentation on the OpenStack page is fairly out of date. There are
also issues with the non-OpenStack, third parts of the upgrade.

One speaker is aiming to produce upgrade documentation that affects
all the services, and not just nova.

Operators desire an ability to rapidly roll-back an upgrade in the
event of a failure. The question is, roll-back because of a
system failure, or because a customer demanded it?

The desire to restart the database without migrating API's is a
major concern. Ops don't want their databases down while the upgrade
is in progress. SQL, and theoretical data value stores can help.

Ops can try and migrate keystone data to a new, single node, if the
traffic between nodes is fairly light.

Audience Poll
-------------

Someone mentioned something about using a virtual service that is not
in docker. Many operators raised their hands.

Most people have unified nova-api nodes. Containerized deployment and
using a virtual-env for each environment on the node is a helpful
operator strategy (I'm not sure what this is for)

Upgrades?
---------

Can Neutron be upgradeable?

* DVR runs in the background. Is an experimental job. Now good results
  so far
* We are doing multi-node neutron
* There are some improvements for

Cinder?

* Generally the schema migrations are like nova.
* Are data migrations done online or offline? None are done at
  all in Mitaka migrations.

Glance?

* No Glance operators or Devs were here. One speaker suspects
  there is some issue with the artifact repository database structure.

Murano?

* Devs are not planning partial upgrades.

Heat?

.. note::

   One speaker saed they are not sure how useful it is debating the
   appropriate container technology. LXD vs Docker is another session
   worth of content.)

* Heat upgrades work, but needs to be optimised for scale, and have
  database checks or tests.

Rolling Upgrades
----------------

This release saw the trial or rolling upgrade repository. Nova and
Swift have this capacity. PCI device handling during migrations are
definitely not tested at all, in the context of upgrades
and migrations. Someone mentioned talk to the SRIV teams.

Migration testing needs to be PCI, advanced networking CI, and a
focus on migration aspects of things. Multi-node testing also
needed. I did not hear what specifcally **needs** this testing.

----

Session #2 Netapp and SolidFire
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

The speaker for this presenation was Chris Ferraro from FICO.

For meeting storage challenges and SLA's, Ceph is a scalable storage
deployment. Ceph provides general block storage. FICE plan to evaluate
and add swift as another storage service.

Why Solid fire?
---------------

* Deployment speed
* Integration
* Solid fire and netapp integrates with VMWare and
  Openstack Cinder. (They have some legacy customers)

Plans for future storage with OpenStack

* Swift as a Service for their developers
* Cinder Shared Storage Volumes use cases are planned
* The tooling Stack will be enhanced - "operation sources are still being sorted" "once deployed, how do you keep operations running?"
* "How can our self service..." (I unfortantely missed the rest of his sentence. Apologies)

History
-------

FICO's founder was at Rackspace, and then started their own business.
They wanted to solve storage problems.

 **"We don't want to be the Uber of storage devices..
 ..We want to solve the noisy neighbour problem".**

"Fibre channel vs ISCSI"
------------------------

State of Storage:

* Containers - Kubernates will standardise containers. economise containers.
* Software defined storage
* Bi-Modal IT - "Thestrain(sic) of appealing to both ends of the spectrum"
* Ease and barriers to adoption

----

Session #3 OpenStack: Meet the personas
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

.. note::

   I arrived a bit later to this session, since the walking distance
   between the previous session and this one was lengthy.

Roles in IT are complicated, and there are different types of business
relationships and responsibilities. Personas are an industry standard.

Admins versus users
-------------------

* Specify Resource Usage Request. (RUR)

.. code:: html

   review.openstack.org/#/c/309567

A review on the personas. The UX team are closely documenting the
personas with the docs project. Their goal is to tailor the personas,
and see them used throughout the project.

Readers and contributors could apply personas to development design
decisions, use personas as IA resources for new and changed guide
evaluation requirements, and recruited for possible marketing
collateral.

----

Session #4 Converting the API docs to RST format
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

No one has taken on structural changes in the waddle docs.

The working theory is that there is an emerging specification standard, which
is an API design language.

This is important for solving why things don't work for us.

Sphinx and rst markup is an easier language. However the API docs need a
tailored and structured format that automates rewriting variables.

The Swagger docs plan literally could not work for about 45% of the
products.

At the moment, the API teams are at a stage where they have created a
couple of new Sphinx standards describing methods and parameters.

:command:`api -i` command.

"Users first, and not contributors first"

There is a reason this is in the source doc tree and not the sample
tree.

We can do a  :command:`literal --include` for all the files.

We need it to be in the sphinx tree for this reason. If you want to
reference a JSON schema in the code tree, you're going to need
a literal reference during the build.

Questions
---------

Is there an option to have the reference in the code tree?

With the nova repo, will we offer reviews? A contributors say yes.
And there is capacity to treat each service API with docs
attention and reviews.

"There's no perfect one source of truth right now"

There is code that runs stuff through JSON schemas. The code tries to
help as a cross reference for doing this correctly. Try and apply JSON
schema to the information available now. This prevents inconsistency.

Reviewers have to be able to understand different domain languages,
including the text itself and JSON.

----

Session #5 Confronting Complexity
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

To handle complexity, we need to recognise OpenStack's pain points,
and talk through initiatives in the community.

Personas
--------

* End Users and App writers
* Business is deploying OpenStack
* Operators of OpenStack cloud

This talk focuses on Operators
------------------------------

Quotes from operators:

* "I'm going to have to manage this thing [constantly]"
* "Too many core components"
* "OpenStack is not a polished product"

How do End Users Choose a project that sits outside the big tent?

The weight of 54 items in the big tent is an issue.

Community activities for solving complexity

One solution to complexity: DOCS
--------------------------------

Also, API's create request IDs in API responses. These are storred as
logs. The user can view these logs to find some troubleshooting solutions.

The UX - User Experience work group -  are detailing the operator and
other personas to improve the experience of the operator.

Curation
^^^^^^^^

Corporate and Community teams create automated services that are
curated implementations of OpenStack.

We possibly need better documentation of reference architecture. Of all
the different projects, each has a different prescription
for reference architecture.

----

Session #6 OSIC training
~~~~~~~~~~~~~~~~~~~~~~~~

The OSIC team found that a Historical, lecture and note taking
teaching approach does not work well for OpenStack.

The initial class recruited Intel and OpenSoftware Dev talent,
plus high potential uni students.

Contribution skills came first as a bug catching element on
the way through.

Challenges:

* OpenStack talent is rare
* Moving is tough for some
* Where to start? Best bugs or features

Lessons - Learning Moments:

* Global recruiting level - search for talent at a global level. Their
  teams were geographical loctions were broad.
* University level farming - Work directly with the University to
  create an intern program on paid internships.
* "Solar System Model" - One experts exerts gravitational pull onto
   several new developers who are eager to learn. Success results in
   more weight or mass adding to planets.
*  Embrace beginners, and introduce new recruits with a teaching
   oppurtunity to alleviate any stress.
*  "Way of the Stacker" - Teach students how to be successful in
    OpenStack, lowering the barrier how to work within the
    community. +2 +1, reviews, specs, blueprints, mailing lists,
    and IRC.

.. warning::

   A short **video** followed at this point. See ***OSIC - lessons
   learned in building the world's largest OpenStack Developer Cloud**

A Quote from one of the students:
---------------------------------

"After training with OSIC, I know what I 'don't know'".

OSIC - The Future

* Talent replication - first graduates return to teach.
* Break up the 3 week classes into smaller items
* Deep dives into specific services
* recruit supporting coding skills.
* Onboard new developers outside just Rackspace and OSIC.
* "Target Tutoring" Session helped talent to become more
  expert such that they could pass the assessment challenges.

OSIC Dev lounge was on the 4th floor of the Hilto accross from the
Austin Convention Center.

There is a 1000 node cluster at OSIC.org.

----

Session #7 Summit Reorganisation: splitting design sessions
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

This session concerned the proposed chaged to summit timing.

Question:
---------

Would the release change? May and November release rather than having a
release that aligns with a summit.

The summit would happen 2 months after the release.

Travel budgets need to allow for no more than one event
per quarter for those travelling.

Keep the weeks in advance free to give as much notice as possible.

This gives people a chance to rearrange their schedules and prepare for
travel.

Outside North America, summits are more expensive for many travllers.

There will be some light sponsorship opportunities to adjust costs.

The events will be ticketed.

You buy the ticket to the PGT, you get a free summit ticket too, if you attend.

The weeks leading up to release are hectic - we need to make sure there
is time available for final checks and last minute item.

We also need lead time to properly articulate discussion points. It
takes time for users and developers to turn observations into questions,
and action items.

Why aren't we talking about R- if the attempt is to have no midcycles?
We are having midcycles.

There is still a place for midcycles in some projects.

See https://etherpad.openstack.org/p/newton-design-summit-format

Observations
^^^^^^^^^^^^

"Midcycle was the most valuable and productive time with my team".

"This sounds like we are going from 4 productive meetings to 2 meetings".
