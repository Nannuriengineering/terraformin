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
-it will download all the plugins related to provider what we mentioned in the provider
terraform plan
--------------------
it will display what all changes its going to do.and also any errors in the code we had written

terraform apply --auto-approve
-----------------------------



terrsform files:
-----------------------------
.tf
.state
.tfvars

if it has .tf file it will consider as terraform file.

provider must be put in main.tf



