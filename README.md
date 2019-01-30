infrastructure
==============

This role may be used to build and maintain infrastructure via Terraform.

Requirements
------------

Requires terraform to be installed on the target host.

Role Variables
--------------

* `infrastructure`: An array of infrastructure values, each of which has the following keys:
  * `file`: The Terraform resource filename (without the `.tf` extension) to be built.
  * `task`: The resource type (corresponding to a `.yml` file in the [`tasks`](tasks) directory.
  * ... : Other key/value pairs may be present, which are passed to the relevant ansible plugin.
  * `terraform` : A dict of `name` -> `values` for each terraform resource to be listed within this file.
    * *resource-name* : The terraform name for this resource.
	  * `arg` : The resource argument whose data value will be used to discover whether this resource already exists.
	  * `match` :
	    * If `arg == 'count'`, this is a regular-expression applied against a `tag` value to match existing resources.
		* Otherwise, this is the field returned by an ansible facts plugin that corresponds to the resource `arg`.
	  * `replace` : Used with `match` to extract the count index from a `tag` value. Ignored if `arg != 'count'`.
	  * `tag` : The AWS tag name used for finding resources generated with `arg == 'count'`.
      * `yaml` : A dict describing the resource to be created or updated, which is passed to Terraform.

Dependencies
------------

See [`meta/main.yml`](meta/main.yml).

Example Playbook
----------------

TBD

To-Do
-----

TBD

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
