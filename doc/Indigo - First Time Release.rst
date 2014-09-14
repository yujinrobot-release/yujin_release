.. highlight:: bash

Indigo - First Time Release
===========================

Preparation
-----------

The following uses the hypothetical repo ``foo``.

* Create a `new repository`_ called _foo-release_.
 * Initialise it with a README.
* Clone the release repository locally and configure it with bloom for indigo.

.. code-block:: bash
    > git clone https://github.com/yujinrobot-release/foo-release
    > cd foo
    > bloom-release --rosdistro indigo --track indigo foo --edit

Options to configure:

* First provide a link to the release repo to get it started: `https://github.com/yujinrobot-release/foo-release.git`
* *Repository Name*: foo
* *Upstream Repository URI*: url to your code repo, e.g. `https://github.com/stonier/foo.git`
* *Version*: :{auto}
* *Release Tag*: :{version}
* *Upstream Devel Branch*: usually 'indigo'
* *ROS Distro* : indigo
* *Patches Directory* : None
* *Release Repository Push URL*: None (it will use your first supplied release URI by default)
* *Releasing Complete, push?* : yes
* *Add Documentation?* : yes if you have sphinx/doxygen organised, no otherwise.
* *Add Source Information?* : yes, this lets you pre-release test off the latest commits
* *Add Maintenance Status?* : yes, either 'maintained' or 'developed'.


.. _`new repository`: https://github.com/organizations/yujinrobot-release/repositories/new
