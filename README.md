
<!-- PROJECT LOGO -->
<br />
<p align="center">
  <a href="https://github.com/othneildrew/Best-README-Template">
    <img src="images/logo.png" alt="Logo" width="80" height="80">
  </a>

  <h3 align="center">Ogli</h3>

  <p align="center">
    Ogli is a tool to quickly build APIs up in Amazon's AWS Cloud
    <br />
    <a href="https://docs.ogli.io/"><strong>Explore the docs »</strong></a>
    <br />
    <br />
    <a href="https://www.youtube.com/watch?v=i7KFJFIn4mQ&feature=emb_logo">View Demo</a>
    ·
    <a href="https://github.com/ogli-api/ogli/issues">Report Bug</a>
    ·
    <a href="https://github.com/ogli-api/ogli/issues">Request Feature</a>
  </p>
</p>

<!-- TABLE OF CONTENTS -->
## Table of Content

* [TL;DR](#tl-dr)
* [What is Ogli?](#what-is-Ogli)
* [Getting Started](#getting-started) 
  * [Installation](#installation)
    * [Ogli](#ogli)
  * [Usage](#usage)
    * [Creating your first project](#creating-your-first-project)
    * [Command Line Interface (CLI)](#command-line-interface)
    * [How to create an API](#how-to-create-an-api)
    * [How to create a Flow](#how-to-create-a-flow)
  * [Testing and Debugging](#testing-and-debugging)
* [Connectors](#connectors)
* [Building a Custom Component](#building-a-custom-component)
* [FAQ](#faq)

## :zap: TL;DR 

> :star: Ogli is a Simple, Serverless, Integration and API creation tool and framework.

## What is Ogli?

The Ogli command line interface (CLI) is used to create serverless application integration projects and APIs that run 
in the cloud on Amazon's AWS platform. Ogli is a "deploy first" framework. Instead of deployment being the last thing 
you do, with Ogli it is the first thing you do. Deployment is something you are always doing, so it should be as natural 
as possible (not something to be feared).

## Getting Started

### Installation

1. **Create your own AWS account:**  Given `Ogli` allows us to handle AWS deploys, you must have your own Amazon AWS account. To create one, just 
[click here](https://aws.amazon.com/account/).

2. **Configure asw-cli:** Once you have your own AWS account, you must configure it before Ogli will work. 
[Here](https://docs.aws.amazon.com/cli/latest/userguide/cli-chap-configure.html) you will find how to configure the 
AWS CLI.

3. **Configure ogli:** the following file needs to go in your home folder:
    * Unix: `~/.ogli.yml` 
    * Windows: `C:\Users\username\.ogli.yml`
    
    ```yaml
    ogli:
      company: acme # PUT A NAME HERE WITH NO SPACES, MUST BE UNIQUE
      
      profiles:
        - default:   # Name of the AWS profile.  You can change this.
            account: '123456789' # PUT YOUR AWS ACCOUNT ID HERE'
            region: us-east-1   # PUT YOUR REGION HERE ex: no hyphens
            environment: dev   # Name of the ogli environment. You can change this
    
    # if you want to configure another profile, just copy the default one and edit.
      
      layer_account: '987654321'  # OGLI WILL PROVIDE THIS
      layer_version: 341   # You may need to update this from time to time
      
      # do not modify these for now
      log:
        logging: DEBUG
      library_name: oglilib
      runtime: python3.7
      kms_key_alias: ogli
      main_lambda_timeout: 300
      start_lambda_timeout: 300
      lambda_role: OgliAccess
      start_file_sizing:
        min_size_to_split: 1000000
        chunk_size: 500000
        max_files: 50
    ```

#### Ogli
1. **Create a virtual environment (recommended):** `Ogli` is distributed as a python package, so you can installed 
directly in your machine or better, in a python virtual environment. You can create your own venv any way you like. Here is an example:

    ```sh
    $ python3 -m venv ./.env/ogli 
    $ source ./.env/ogli/bin/activate 
    $ pip install --upgrade pip
    ```

2. **Install wheel pachage**: use the package manager [pip](https://pip.pypa.io/en/stable/) to install ogli:
`$ pip install --upgrade ogli-0.0.1-py3-none-any.whl`

3. **Configure aws-ogli:** `$ ogli configure-aws`

> NOTE: If you don't want to install Ogli on your computer/laptop, then you can install it on an online account at 
> [Python Anywhere](https://www.pythonanywhere.com/)

 
### Usage

#### Creating your first project
TODO

#### Command Line Interface (CLI)

A summary of commands and actions can be found in the following table:

| Command | Action |
| ------ | ------ |
| clean | clean controller |
| unconfigure-aws | opposite of configure-aws |
| clean-folder | empty folder |
| cp (create-project) | create a project |
| TODO | TODO |


#### How to create an API
TODO

#### How to create a Flow
TODO

### Testing and Debugging 
TODO

## Connectors
* **Slack:** Post body of message to slack and post exceptions to slack
* **Dynamodb:** Put data into and get data from a Dynamodb table
* **Delimited Reader:** The delimited_reader will read in a flat file that is delimited by a single character
* **Delimited Writer:** Writes out body in a delimited file format
* **Xml Reader:** Reads in xml and converts to a Python dictionary or list.
* **Xml Writer:** Writes out the current body to xml
* **Http Get:** Perform an http get on a resource
* **Http Post:** Post the body of the message to an http resource
* **Jdbc:** There are currently two jdbc components: jdbc_insert and jdbc_select

## Building a Custom Component
TODO

## FAQ
* How do you pronounce Ogli?
    > Ogli is pronounced: oh-glee
                               
* What do you do if there isn't a built-in component in Ogli that does what you need it to do?
    >  Ask us and see if we actually do have one that does something similar or we are working on one.  We may put it in our backlog todo list.

    > * Create your own component that can do it.

    > * If it is not possible to do what you want with an Ogli custom component, then you could create your own Lambda that does what you need and then integrate your flows with that Lambda.

## Contributing
Pull requests are welcome. For major changes, please open an issue first to discuss what you would like to change.

## License
TODO

## Contact
TODO
