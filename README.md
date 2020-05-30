
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

[![PRs Welcome](https://img.shields.io/badge/PRs-welcome-brightgreen.svg?style=flat-square)](http://makeapullrequest.com)

<!-- TABLE OF CONTENTS -->
## 🚩 Table of Content
* [TL;DR](#zzz-tldr)
* [What is Ogli?](#bowtie-what-is-ogli)
* [Getting Started](#rocket-getting-started) 
  * [Installation](#installation)
    * [Ogli](#ogli)
  * [Usage](#ballot_box_with_check-usage)
    * [Creating your first project](#creating-your-first-project)
    * [Command Line Interface (CLI)](#command-line-interface)
    * [How to create an API](#how-to-create-an-api)
    * [How to create a Flow](#how-to-create-a-flow)
  * [Testing and Debugging](#testing-and-debugging)
* [Connectors](#electric_plug-connectors)
* [Building a Custom Component](#coffee-building-a-custom-component)
* [FAQ](#faq)
* [Contributing](#busts_in_silhouette-contributing)
* [License](#blue_book-license)
* [Contact](#postbox-contact)

## :zzz: TL;DR 

> Ogli is a Simple, Serverless, Integration and API creation tool and framework.

## :bowtie: What is Ogli?
Ogli is a "deploy first" framework. Instead of deployment being the last thing you do, with Ogli it is the first thing 
you do. Deployment is something you are always doing, so it should be as natural as possible (not something to be feared).
The Ogli command line interface (CLI) is used to create serverless application integration projects and APIs that run 
in the cloud on Amazon's AWS platform.
 
## :rocket: Getting Started

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

> :warning: If you don't want to install Ogli on your computer/laptop, then you can install it on an online account at 
> [Python Anywhere](https://www.pythonanywhere.com/)

 
### :ballot_box_with_check: Usage

#### Creating your first project
A `project` is a group of flows (workflows). A project has a property file containing name/value pairs. The properties 
are available to all of the flows in that project. A project has one or more flows (workflows). A flow takes an input 
does some processing on it and optionally generates an output. A project has a Main folder and a Main function. 
When a file is created in the Main folder, it will trigger the Main function which will then process the file.

Use the commands below to create your first project: `$ ogli cp project1`

Here is a sample project file. It has information about all of the assets in the project and the project flows:

```json
{
    "name": "processcsv",
    "company": "mycompany",
    "folders": [
        "main",
        "error"
    ],
    "functions": [
        "main"
    ],
    "flows": {
        "loadcsv": {
            "name": "flow1",
            "format": "delimited",
            "folders": [
                "start",
                "end",
                "error"
            ],
            "functions": [
                "start"
            ]
        }
    }
}
```

Here is a sample property file.
```json
{
   "property1": "one",
   "property2": "two"
}
```

#### Command Line Interface (CLI)

A summary of commands and actions can be found [HERE](https://docs.ogli.io/untitled-1/cli).

#### How to create an API
Video outlining the steps to create an API with Ogli: [video](https://www.youtube.com/watch?v=yI_m8xe8hCA&feature=emb_logo)



#### How to create a Flow
Video outlining the process of creating an Ogli file flow (workflow): [video](https://www.youtube.com/watch?v=i7KFJFIn4mQ)


### Testing and Debugging 

#### Testing
Here is how you test with ogli:

* **To test a flow:** `$ ogli test [flow name]`

* **To see what happened, what a second and then run:** `$ ogli info`

* **If you see files in the main folder, then there was probably an issue. To see the main log:** `$ ogli logs main`

* **To see the start log for a flow:** `$ ogli logs flow1-start`

* [Integration testing](https://docs.ogli.io/integration-testing)


#### Debuggig tips
Here are some tips to help you debug your flows:

* When you test a flow, it pushes that flow. If you are testing a flow that connects to other flows and you made changes 
to those flows, then you need to push them.

* Work with small data files until you know the flow is working correctly.  If you are working with a list of records, 
then delete all records except for a few and see what happens.

* One way to work with smaller data sets is to filter out most of the records. This example will only let records with 
the state = 'OK' pass:

    ```json
    {
        "component": "ogli.filter",
        "expression": "body['state'] == 'OK'"
    }
     ```

* You can disable a component (toggle off, skip) but adding a 'run_if' parameter and setting it to "False".  The *run_if* 
parameter takes an expression and all expressions must be in double quotes.

* When a component is disabled, the messages pass through the component untouched.

## :electric_plug: Connectors
* **Slack:** Post body of message to slack and post exceptions to slack
* **Dynamodb:** Put data into and get data from a Dynamodb table
* **Delimited Reader:** The delimited_reader will read in a flat file that is delimited by a single character
* **Delimited Writer:** Writes out body in a delimited file format
* **Xml Reader:** Reads in xml and converts to a Python dictionary or list.
* **Xml Writer:** Writes out the current body to xml
* **Http Get:** Perform an http get on a resource
* **Http Post:** Post the body of the message to an http resource
* **Jdbc:** There are currently two jdbc components: jdbc_insert and jdbc_select

## :coffee: Building a Custom Component
If there is not a built-in component to do the task you need done, then you can easily build your own custom component 
using Python.

In the following example, we will build a custom component that will take a flat car data and transform it into a 
more hierarchical format.

Input example:

```json
{
    "id": "bb9db8",
    "year": 2014,
    "make": "BMW",
    "model": "i8",
    "class": "Subcompact Cars",
    "cylinders": 3,
    "displacement": 1.5,
    "drive": "All-Wheel Drive",
    "fuel_type": "Premium and Electricity",
    "transmission": "Automatic 6-spd",
    "mpg_highway": 29,
    "mpg_city": 28
}
```

Expected output:

```json
{
    "id": "bb9db8",
    "type": {
        "year": 2014,
        "make": "BMW",
        "model": "i8",
        "class": "Subcompact Cars"
    },
    "details": {
        "engine": {
            "cylinders": 3,
            "displacement": 1.5
        },
        "transmission": {
            "type": "Automatic 6-spd",
            "drive": "All-Wheel Drive"
        }
    },
    "fuel": {
        "type": "Premium and Electricity",
        "mpg": {
            "city": 28,
            "highway": 29
        }
    }
}
```
 
See the full custom component implementation [here](custom-component.md).





## :question: FAQ
* How do you pronounce Ogli?
    > Ogli is pronounced: oh-glee
                               
* What do you do if there isn't a built-in component in Ogli that does what you need it to do?
    >  Ask us and see if we actually do have one that does something similar or we are working on one.  We may put it in our backlog todo list.

    > * Create your own component that can do it.

    > * If it is not possible to do what you want with an Ogli custom component, then you could create your own Lambda that does what you need and then integrate your flows with that Lambda.

## :busts_in_silhouette: Contributing
Pull requests are welcome. For major changes, please open an issue first to discuss what you would like to change.

## :blue_book: License
TODO

## :postbox: Contact
Shane Berry 
