terraform functions:
-----------------------

list:
-----------

element:
------------------
element(list, index)--index=count

https://www.terraform.io/docs/language/functions/element.html

splat syntax:
-----------------
https://www.terraform.io/docs/language/expressions/splat.html

map
count
count.index
length
lookup:
--------------------
https://www.terraform.io/docs/language/functions/lookup.html
 condition  ? true :false:
---------------------------------------
var.env==prod ? 3 : 1

count=var.env==prod ? 3 : 1


