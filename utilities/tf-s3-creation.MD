#To set this up using terraform remote state, I usually have a separate folder called remote-state within my dev and prod terraform folder.

#The following main.tf file will set up your remote state for what you posted:

provider "aws" {
  region = "us-east-1"
}

resource "aws_s3_bucket" "tf_state" {
  bucket = "tfstatek"

  versioning {
    enabled = true
  }

  lifecycle {
    prevent_destroy = false
  }
}


prevent_destroy =true while creating. When deleting, or destroying, need to put false
