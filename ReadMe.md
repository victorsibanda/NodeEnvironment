# Node Environment AMI Builder

This repository allows you to create an Amazon Machine Image (AMI) using packer and this image can be used to create EC2's instances which have the App installed and setup for use with a database.

## What is Packer

Packer is an open source tool, from Hashicorp which allows you to create Identical Machine Images from a a single source file. In this directory that is `packer.json`. Packer can use Chef or Puppet, which are configuration management tools, to provision the required packages onto your machine. In this machine I have used Chef and a chef cookbook.

## Prerequisites

- AWS Access Key and ID
 - Should be added as Environment variables into your .bashrc/.profile/.zshrc
 - variables should be named 'AWS_ACCESS_KEY_ID' and 'AWS_SECRET_ACCESS_KEY' to be used with the current `packer.json`


- Amazon Key-Pair (The `packer.json` does not include a key-pair but you can create one when you make your instance)
- Packer
- Chef

#### Packer Installation

https://www.packer.io/downloads.html

If you have Homebrew installed use  `brew install packer`

#### Chef Installation

https://docs.chef.io/workstation/install_workstation/

To use Chef you have to accept the chef licence done by adding

`export CHEF_LICENSE="accept"` into your .bashrc/.profile/.zshrc



## Usage


- To begin clone the repository
`git clone git@github.com:victorsibanda/NodeEnvironment.git`

- In terminal use `berks vendor Cookbooks`
which will clone the cookbooks into a folder named Cookbooks.


Note :: If you want to repeat the process use `rm berksfile.lock`
then run `berks vendor Cookbooks` again.

- To create the AMI Run :
 `packer validate packer.json`

 - If that passes run:

  `packer build packer.json`
