#####################################################################################################
Verification of the correct functioning of the M2 axial and tangent actuators in the closed-loop mode
#####################################################################################################

.. abstract::

   This technote is the description for the test case is to verify the correct functioning of the axial actuators in the closed-loop mode by assessing the linear relation between  forces and motor steps.

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
* `LVV-18742 <https://rubinobs.atlassian.net/browse/LVV-18742>`_: the test case of the verification o.
* LVV-T2969 (LVV-E3398): M2 outer control loop: closed-loop mode for axial actuators.  

Related Requirements
====================
* **LTS-146-REQ-0159** : 3.5.9 Mirror Tangent Actuator (Link) Control

    Specification: The tangent links SHALL function as two opposite sets of kinematic supports.

* **LTS-146-REQ-0160** : Outer Control Loop

    Specification: The outer control loop SHALL determine the command forces for all the axial actuators of the M2 mirror support system and convert them into motor steps in order to command the inner loop controllers. In closed-loop mode, it sends force commands to a single axial actuator and a single tangent link to verify the outer control loop converts the command forces into motor steps.

Execution Details and Data
==========================

Background and Information
--------------------------
.. figure:: /_static/figures/M2_actuator_map.png
   :scale: 80%

Outer Loop Control Test For Tangent Links
-----------------------------------------
This verification test of M2 surrogate on the cart was proceed on Jun 14th, 2023 at Level 3. All steps were done sucessfully.  

1. Sanity check on the script by commanding a single forces manually to tangent actuator closed loop on A1.

    * 21:35:30 UTC: command +20 N to A1 tangent link
    * 21:37:30 UTC: command -20 N to A1 tangent link
    * 21:39:30 UTC: command +50 N to A1 tangent link
    * 21:41:35 UTC: command -50 N to A1 tangent link
    * 21:43:30 UTC: command +100 N to A1 tangent link
    * 21:45:30 UTC: command -100 N to A1 tangent link

2. 21:48:27 - 21:57:33 UTC: Sequence on A1 tangent link

3. 23:26:19 - 23:35:25 UTC: Sequence on A2 tangent link

4. 23:36:39 - 23:45:45 UTC: Sequence on A3 tangent link

5. 23:49:58 - 23:59:04 UTC: Sequence on A4 tangent link

6. 00:00:37 - 00:09:43 UTC: Sequence on A5 tangent link

7. 00:13:36 - 00:22:42 UTC: Sequence on A6 tangent link


Outer Loop Control Test For Axial Links
----------------------------------------
This verification test was done on November 8th, 2023. 
It happened with SAL script run_bump_test through the notebook.
On each force actuator, first apply force of -150N, -100N, -50N, 50N, 100N, and 150N. 
After applying each force, the applied force was reset.  

1. On the axial actuator 9 (B10): Bump test started at 20:11:39 UTC.

2. On the axial actuator 32 (C3): Bump test started at 20:20:49 UTC. 

3. On the axial actuator 70 (D17): Bump test started at 20:29:58 UTC


Results
=======


Outer Loop Control Test For Tangential Links
--------------------------------------------

Demanded forces on each tangential link are defined as below:


.. math::
    F_{D} = F_{LUT} + F_{ap} + F_{HP_{corr}}



Forces and Steps with respect to Time
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

.. figure:: /_static/figures/Time_vs_Forces_and_Step_on_A1.png
    :name: TS-A1

    Forces and Steps on Tangential Link A1. 


.. figure:: /_static/figures/Time_vs_Forces_and_Step_on_A1_Zoom_in.png
    :name: TS-A1-Zoom-in
 
    Zoomed-in figures for forces and steps on tangential link A1. 
    (Left) An example of intervals where standard deviation was computed.
    (Middle) An sampled interval of inaccurate telemetry.
    (Right) Same as Left, but an interval with smalller standard deviation. 
    Note that most intervals show similar amount of this example.  

 
.. figure:: /_static/figures/Time_vs_Forces_and_Step_on_A2.png
    :name: TS-A2
 
    Forces and Steps on Tangential Link A2. 

.. figure:: /_static/figures/Time_vs_Forces_and_Step_on_A3.png
    :name: TS-A3
 
    Forces and Steps on Tangential Link A3. 

.. figure:: /_static/figures/Time_vs_Forces_and_Step_on_A4.png
    :name: TS-A4
 
    Forces and Steps on Tangential Link A4.

 
.. figure:: /_static/figures/Time_vs_Forces_and_Step_on_A5.png
    :name: TS-A5
 
    Forces and Steps on Tangential Link A5. 


.. figure:: /_static/figures/Time_vs_Forces_and_Step_on_A6.png
    :name: TS-A6
 
    Forces and Steps on Tangential Link A6. 


Demanded Forces and Measured Forces
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

 
.. figure:: /_static/figures/Step_vs_Forces_on_A1.png
    :name: SF-A1
    :scale: 80%

    A correlation between step and demanded force (  measured force Forces and Steps on Tangential Link A1. 

.. figure:: /_static/figures/Step_vs_Forces_on_A1_excluded.png
    :name: SF-A1-excluded
    :scale: 80%
    
    Same as :numref:`SF-A1`, but excluding intervals of 

.. figure:: /_static/figures/Step_vs_Forces_on_A3.png
    :name: SF-A3
    :scale: 80%

    Same as :numref:`SF-A1` but for tangential axis A3. 
  
.. figure:: /_static/figures/Step_vs_Forces_on_A5.png
    :name: SF-A5
    :scale: 80%
    
    Same as :numref:`SF-A1` but for tangential axis A5. 


Outer Loop Control Test For Axial Links
---------------------------------------

.. figure:: /_static/figures/Time_vs_Forces_and_Step_on_B10.png
    :name: TS-B10

.. figure:: /_static/figures/Time_vs_Forces_and_Step_on_C3.png
    :name: TS-C3


.. figure:: /_static/figures/Time_vs_Forces_and_Step_on_D17.png
    :name: TS-D17

..
    _static/figures/Step_vs_Forces_on_B10.png			_static/figures/Time_vs_Forces_and_Step_on_A5.png
    _static/figures/Step_vs_Forces_on_C3.png			_static/figures/Time_vs_Forces_and_Step_on_A6.png
    _static/figures/Step_vs_Forces_on_D17.png			_static/figures/Time_vs_Forces_and_Step_on_B10.png
    _static/figures/Time_vs_Forces_and_Step_on_C3.png
    _static/figures/Time_vs_Forces_and_Step_on_D17.png
   



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
