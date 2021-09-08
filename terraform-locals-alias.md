terraform maps:
----------------
https://www.terraform.io/docs/language/functions/map.html

ex:var.amis["us-east-1"]

terraform locals:
---------------------
https://www.terraform.io/docs/language/values/locals.html

terraform dynamic blocking:
---------------------------

https://blog.boltops.com/2020/10/05/terraform-hcl-loops-with-dynamic-block

https://www.terraform.io/docs/language/expressions/dynamic-blocks.html

https://www.hashicorp.com/blog/hashicorp-terraform-0-12-preview-for-and-for-each

count vs for_each:
------------------------------

count works on index.if index changes everything changes.
for_each doesnot work on index.it works on each element  from the list work on it.(we will use in locals)

terraform provider alias:
=================================
if you have two different accounts how will you deploy the code ?

we will use alias to deploy the code.

https://medium.com/scalereal/how-to-use-multiple-aws-providers-in-a-terraform-project-672da074c3eb


