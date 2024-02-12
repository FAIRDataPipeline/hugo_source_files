---
weight: 1
title: "Installation"
---

# Installation
The remote registry is a (django)[https://www.djangoproject.com/] REST API and can easily be installed on any server which meets the following requirements.

## Pre-requisites
To install a remote registry you will require the following:

A server caple of running a webserver with the following installed:

### [git](https://git-scm.com/downloads)
Available through package managers such as `apt`, `brew` or `chocolatey`

### [Python 3.8+](https://www.python.org/downloads/)
With `pip` and the `venv` module installed.
Available through package managers such as `apt`, `brew` or `chocolatey`

### A database
Such as `PostgreSQL`(recommended), `MariaDB`, `MySQL`, `Oracle`, `SQLite` (not recommended for production). Full database support can be found on the [django site](https://docs.djangoproject.com/en/5.0/ref/databases/)

### [`Graphviz`](https://graphviz.org/)
`Graphiz` is needed to create provernance reports, full installations instructions can be found on the [`Graphviz` site](https://graphviz.org/download/)

## Installation on a Debian based system e.g. Ubuntu
This installation guide will focus on debian based systems but can be easily adapted.

### Step 1. Clone the repository
Clone the dataregistry repository using `git`

```
git clone https://github.com/FAIRDataPipeline/data-registry.git
```

### Step 2. Create and activate a Python virtual environment (`venv`) in the repository folder

```
python3 -m venv venv
source venv/bin/activate
```

### Step 3. Install the `python` requirements

```
pip3 install -r local-requirements.txt
```
***N.B.*** the local requirements match the remote requirements

### Step 4. Generate a secret key

```
python3 -c 'from django.core.management.utils import get_random_secret_key; print(get_random_secret_key())'
```

### Step 5. Edit drams/settings.py
The `settings.py` file within the `drams` folder should be modified to match your requirements.

#### Add your secret key
The secret key you generated in the previous step can either be added directly to the `settings.py` file:

```
SECRET_KEY = '<generated secret key>'
```
**N.B** If you do this remember to remove the following lines:
```
with open('/home/ubuntu/secret_key.txt') as f:
    SECRET_KEY = f.read().strip()
```

Alternatively the secret key can be stored in a file and read. To do this edit the following line with the file path a text file containing your secret key:
```
with open('/home/ubuntu/secret_key.txt') as f:
    SECRET_KEY = f.read().strip()
```

### Edit `ALLOWED_HOSTS`

Add your domain to `ALLOWED_HOSTS` replacing `data.fairdatapipeline.org`

### Optional

If you wish to use caching install and setup PyLibMCCache.