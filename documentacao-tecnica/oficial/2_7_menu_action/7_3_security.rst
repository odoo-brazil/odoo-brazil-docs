Security
========

Three concepts are differentiated into OpenERP;

   1. The users: person identified by his login/password
   2. The groups: define the access rights of the resources
   3. The roles: determine the roles/duties of the users 

.. figure::  images/module_base_user.png
   :scale: 120
   :align: center


**The users**

They represent physical persons. These are identified with a login and a password. A user may belong to several groups and may have several roles.

A user must have an action set up. This action is executed when the user connects to the program with his login and password. An example of action would be to open the menu at 'Operations'.

The preferences of the user are available with the preference icon. You can, for example, through these preferences, determine the working language of this user. English is set by default.

A user can modify his own preferences while he is working with OpenERP. To do that, he clicks on this menu: User > Preferences. The OpenERP administrator can also modify some preferences of each and every user.

**The groups**

The groups determine the access rights to the different resources. There are three types of right:

    * The writing access: recording & creation,
    * The reading access: reading of a file,
    * The execution access: the buttons of workflows or wizards. 

A user can belong to several groups. If he belongs to several groups, we always use the group with the highest rights for a selected resource.

**The roles**

The roles define a hierarchical structure in tree. They represent the different jobs/roles inside the company. The biggest role has automatically the rights of all the inferior roles.

**Example:**

CEO

  + Technical manager

    - Chief of projects

      - Developers
      - Testers

  + Commercial manager

      - Salesmen
      - ...

If we want to validate the test of a program (=role Testers), it may be done by a user having one of the following roles: Testers, Chief of the project, Technical manager, CEO.

The roles are used for the transition of Workflow actions into confirmation, choice or validation actions. Their implications will be detailed in the Workflow section. 


Menu Access
-----------

It's easy (but risky) to grant grained access to menu based on the user's groups.

First of all, you should know that if a menu is not granted to any group then it is accessible to everybody ! If you want to grant access to some groups just go to **Menu > Administration > Security > Define access to Menu-items** and select the groups that can use this menu item.

.. figure::  images/grant_access.png
   :scale: 85
   :align: center

Beware ! If the Administrator does not belong to one of the group, he will not be able to reach this menu again. 
