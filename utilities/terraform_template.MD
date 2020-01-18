
resource "aws_instance" "web-server" {
  ami = "ami-011b3ccf1bd6db744"
  instance_type = "t2.micro",
  key_name = "bt_keypair1"

tags {
    Name = "first-chapter-test"
  }


  provisioner "remote-exec" {
      inline = [
        "sudo yum -y update",
        "sudo yum -y install httpd",
        "sudo systemctl start httpd",
      ]
  }

  provisioner "file" {
   content     = "ami used: ${self.ami}"
   destination = "/tmp/file.log"
 }
connection {
    type     = "ssh"
    user     = "ec2-user"
    private_key = "${file("bt_keypair1.pem")}"
  }


}
output "instance" {
  value = "${aws_instance.web-server.id}"
}

output "ip" {
  value = "${aws_instance.web-server.public_ip}"
}
