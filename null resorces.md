null resource and taint usage:
---------------------------------------
in normal cases the userdata will executed only once when we deploying the ec2 machine.if you want execute changing script it wont happen again.you need to delete the ec2 
and run the terraform again.

https://www.terraform.io/docs/language/resources/provisioners/file.html

but i dont want it delete machine when every time script changing.to acheive this we will use null resources.

prrovisioner "file" { ------------------to copy the file into server
  source = "script.sh"
  destination = "/tmp/script.sh"
  connection {
  type = "ssh"
  user = "ubuntu"
  private_key = "${file("labtap.pem")}"
  host = "${aws_instance.web-1.public_ip}" ------"${element(aws_instance.web-1.*.public_ip,count.index)}"
  }
  }
  
  to execute the script---add down one 
  -----------------------------
  
  provisioner "remote-exec" {
  inline = [
    "chmod +x /tmp/script.sh",
    "sudo /tmp/script.sh",
    ]
    connection {
  type = "ssh"
  user = "ubuntu"
  private_key = "${file("labtap.pem")}"
  host = "${aws_instance.web-1.public_ip}" ------"${element(aws_instance.web-1.*.public_ip,count.index)}"
  }
  }
    
  
  
  add that script in the ec2 macine.create script.sh file and laptap.pem file(private key of file)
  
  
  Taint:
  ------------------------
  
  if you want recreate particular resorce we will use taint.if you taint on a resource it will destroy that particular resoource and recreste it
  
  terraform state list
  
  terraform taint <any resource name>
  -----------------------------------------
  ---------you give taint on a ec2 machine it will destroy and recreate it.but i want only to run script without destroying the ec2 machine 
  so for this we will use null resource.
 
  
to avoid this we will use null resourrce
  
  resource "null_resorce" "<name>"
  {
      count = "${var.environment == "prod" ? 4:1 }"
    provisioner "file" { ------------------to copy the file into server
  source = "script.sh"
  destination = "/tmp/script.sh"
  connection {
  type = "ssh"
  user = "ubuntu"
  private_key = "${file("labtap.pem")}"
  host = "${aws_instance.web-1.public_ip}" ------"${element(aws_instance.web-1.*.public_ip,count.index)}"
  }
  }
  provisioner "remote-exec" {
  inline = [
    "chmod +x /tmp/script.sh",
    "sudo /tmp/script.sh",
    ]
    connection {
  type = "ssh"
  user = "ubuntu"
  private_key = "${file("labtap.pem")}"
  host = "${aws_instance.web-1.public_ip}" ------"${element(aws_instance.web-1.*.public_ip,count.index)}"
  }
  }
}  
  
  
  now you taint the null_resource
  
  terraform taint null_resource.nameof the resource  -------it will destroy the resource and recreate it.
  terraform untaint <resourcename>
