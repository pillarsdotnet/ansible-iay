Infrastructure As Yaml
======================

This role may be used to build and maintain infrastructure via Terraform.

Requirements
------------

Requires terraform to be installed on the target host.

Role Variables
--------------

* `iay`: Infrastructure As Yaml -- the top-level variable name.
  * `aws`: The Terraform provider. For now, only `aws` is supported.
    * `backend`: Terraform state-storage information.
	  * `s3`: For the s3 backend, a bucket/path string.
	* `data`: Terraform data sources.
	* `region`: The AWS region in which to build this infrastructure.
	* `resource`: An array of Terraform resource blocks.
	  * \- (type): The type of resource, without an `aws_` prefix.
	      * (name): The Terraform name of this resource.
		    * (attribute): An attribute for building this resource.
		    * (attribute): A second attribute.
		    * (attribute): A third attribute.
          * (name): The name of another resource with the same type.
		    * (attribute): An attribute for building this resource.
		    * (attribute): A second attribute.
		    * (attribute): A third attribute.
	  * &nbsp; (type): The type of a second resource within the same block.
	      * (name): The Terraform name of this resource.
		    * (attribute): An attribute for building this resource.
		    * (attribute): A second attribute.
		    * (attribute): A third attribute.
	  * \- (type): The type of a resource in a second block.
	      * (name): The Terraform name of this resource.
		    * (attribute): An attribute for building this resource.
		    * (attribute): A second attribute.
		    * (attribute): A third attribute.

This role will loop through the ordered list of resource blocks,
attempting to import each resource with sufficient attributes for
unique identification, before running `terraform apply`.

Dependencies
------------

See [`meta/main.yml`](meta/main.yml).

Example Playbook
----------------

TBD

To-Do
-----

Lots of aws types (not to mention other cloud providers) need to be added to [vars](vars/main.yml).

License
-------

BSD

Author Information
------------------

[Robert August Vincent II](https://github.com/pillarsdotnet)  
*(pronounced "Bob" or "Bob-Vee")*  

