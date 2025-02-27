#####################################################################################################
Verification of the correct functioning of the M2 axial and tangent actuators in the closed-loop mode
#####################################################################################################

.. abstract::

   This technote is the description for the test case is to verify the correct functioning of the axial actuators in the closed-loop mode by assessing the linear relation between measured/applied forces and motor steps.



.. Metadata such as the title, authors, and description are set in metadata.yaml

.. TODO: Delete the note below before merging new content to the main branch.

.. note::

   **This technote is a work-in-progress.**

Introduction
============

Closed-loop control
-------------------
"Closed-loop control" refers to a system where continuous feedback adjusts components in real-time, ensuring optimal performance despite external disturbances like wind or temperature changes then makes precise adjustments to maintain image quality.
 
There are four different control modes for M2:

* **Idle**: idle to set the configuration parameters. 

* **Telemetry-only**: reading the ILC data and doing the publishment only.

* **Open-loop**: under the open-loop control. All ILCs are enabled to read the data and control the actuators. The motor power is on.

* **Closed-loop**: actively doing the actuator movement to adjust the forces to be consistent with the gravity and temperature LUTs. The force balance system is involved in minimizing the moments. The 6 passive hardpoints (3 axial actuators + 3 tangent links) are still. The demanded forces on them will be redistributed to the left 72 active actuators (69 axial actuators + 3 tangent links).

Note that the system should always be under closed-loop control to minimize the stress of the mirror in the normal operation mode. 

Related Tickets and Test Cases
==============================

* `SITCOM-1082 <https://rubinobs.atlassian.net/browse/SITCOM-1082>`_: M2 Verifi. with Surrogate on L3 and TMA - static, quasi-static, dynamic tests - Data Analysis
* `SITCOM-1105 <https://rubinobs.atlassian.net/browse/SITCOM-1105>`_: the ticket linked to this technote. 
* `LVV-18742 <https://rubinobs.atlassian.net/browse/LVV-18742>`_: the test case of this verification 

Related Requirements
====================
* **LTS-146-REQ-0159** : 3.5.9 Mirror Tangent Actuator (Link) Control
Specification: The tangent links SHALL function as two opposite sets of kinematic supports.

* **LTS-146-REQ-0160** : Outer Control Loop
Specification: The outer control loop SHALL determine the command forces for all the axial actuators of the M2 mirror support system and convert them into motor steps in order to command the inner loop controllers. In closed-loop mode, it sends force commands to a single axial actuator and a single tangent link to verify the outer control loop converts the command forces into motor steps.

Execution Details and Data
==========================
This verification test of M2 surrogate on the cart was proceed on Jun 14th, 2023 at Level 3. All steps were done sucessfully.  

1. Sanity check on the script by commanding a single forces manually to tangent actuator closed loop on A1.

* 17:35:30 CLT, 21:35:30 UTC, command +20 N to A1 tangent link
* 17:37:30 CLT, 21:37:30 UTC, command -20 N to A1 tangent link
* 17:39:30 CLT, 21:39:30 UTC, command +50 N to A1 tangent link
* 17:41:35 CLT, 21:41:35 UTC, command -50 N to A1 tangent link
* 17:43:30 CLT, 21:43:30 UTC, command +100 N to A1 tangent link
* 17:45:30 CLT, 21:45:30 UTC, command -100 N to A1 tangent link

2. For loop of commanded forces to tangent actuator closed loop on A1

* 17:48:27 CLT, 21:48:27 UTC, start sequence on A1 tangent link
* 17:57:33 CLT, 21:57:33 UTC, end sequence on A1 tangent link

3. For loop of commanded forces to tangent actuator closed loop on A2

* 19:26:19 CLT, 23:26:19 UTC, start sequence on A2 tangent link
* 19:35:25 CLT, 23:35:25 UTC, end sequence on A2 tangent link

4. For loop of commanded forces to tangent actuator closed loop on A3

* 19:36:39 CLT, 23:36:39 UTC, start sequence on A3 tangent link
* 19:45:45 CLT, 23:45:45 UTC, end sequence on A3 tangent link

5. For loop of commanded forces to tangent actuator closed loop on A4

* 19:49:58 CLT, 23:49:58 UTC, start sequence on A4 tangent link
* 19:59:04 CLT, 23:59:04 UTC, end sequence on A4 tangent link

6. For loop of commanded forces to tangent actuator closed loop on A5

* 20:00:37 CLT, 00:00:37 UTC, start sequence on A5 tangent link
* 20:09:43 CLT, 00:09:43 UTC, end sequence on A5 tangent link

7. For loop of commanded forces to tangent actuator closed loop on A6

* 20:13:36 CLT, 00:13:36 UTC, start sequence on A6 tangent link
* 20:22:42 CLT, 00:22:42 UTC, end sequence on A6 tangent link




Results
=======

Specific analysis block 1
-------------------------
Subsubsection for analysis block 1
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

Tables
------

Plots
-----


Discussion
==========
Conclusion
==========

Related Documentation
======================

Appendix
========


.. Make in-text citations with: :cite:`bibkey`.
.. Uncomment to use citations
.. .. rubric:: References
.. 
.. .. bibliography:: local.bib lsstbib/books.bib lsstbib/lsst.bib lsstbib/lsst-dm.bib lsstbib/refs.bib lsstbib/refs_ads.bib
..    :style: lsst_aa
