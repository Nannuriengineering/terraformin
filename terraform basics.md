it is comes under infrastructure as a code.( IAAS)

aws cloud fromation and azure armtemplates all do the same thing.

Disadvantages of aws cloud formation:
-----------------------------------------

entire code is in single file.
rading the code is complex
dry run is not effective
no module concept
importing resources is not easy.
is not cloud agnostic
creating loops for multiple resources is not easy

terraform advantages:
--------------------------------
distrubute the code in multiple files
resuable code in modules
easy code readbility
terraform plan for dry run is very good
we can import the resoutces easily
we can be used for multiple clouds but code will differnt
terraform functions are good

disadvantages of terraform:
------------------------------------
bugs
plugin might not be availble for latest services.

terraform commands:
-----------------------
terraform version

terraform init
-----------------------
it will download all the plugins related to provider what we mentioned in the provider
terraform plan
--------------------
it will display what all changes its going to do.and also any errors in the code we had written

terraform apply --auto-approve
-----------------------------

terraform validate:
----------------------

to check wether configuration is corrcet or not



terrsform files:
-----------------------------
.tf
.state
.tfvars

if it has .tf file it will consider as terraform file.

provider must be put in main.tf

version is for plugin version.sometimes if you want to use old plugins then we will use version.

syntax:
---------
resource typeof resource nameof resource

ex: resource "aws_vpc" "sravani"{

}


variable.tf we will declare the variables.


by default it will take variables from the tfvars.

if you want specify the variables for differnet environment we use 

terraform plan --var-file prod.tfvars
---------------------------

if you have done some mistakes after applying the infrastructure to get back those changes just use versioning in s3 bucket just go back to the previous version.
or delete the code what you changed and apply again. 

if you have configured the backend in the s3 in the code it will start execuiting the code from the backend.so add the credentials in the backed
#you can soleve this problem two ways.

1. download thw aws cli and configure the credentials there.
2. add the backend.json file write the credenitls in this.


terrform init --backend-config=backend.json
-----------------------------------------
terraform destroy --auto-approve
