infrastructure
==============

This role may be used to build and maintain infrastructure via Terraform.

Requirements
------------

Requires terraform to be installed on the target host.

Role Variables
--------------

* `infrastructure_list`: An array of infrastructure values, each of which has the following keys:
  * `inventory`:
    * `module`: The ansible inventory module used to retrieve a list of already-built objects.
    * `args`: Arguments to be supplied to the above ansible module.
	* `filter`:  A key/value hash used to match one or more objects returned by the inventory module.
	* `min`: The minimum number of objects which should match the above filter.
	* `max`: The maximum number of objects which should match the above filter.
  * `build`:
    * `type`: The type of infrastructure object to build.
	* `args`: A key/value hash describing the object to build.

Dependencies
------------

Example Playbook
----------------

To-Do
-----

License
-------

BSD

Author Information
------------------

Robert August Vincent II  
*(pronounced "Bob" or "Bob-Vee")*  
Office of the Chief Information Security Officer  
U.S. General Services Administration  
Contractor - Team Valiant  
