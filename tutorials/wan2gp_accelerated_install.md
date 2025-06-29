# WAN2GP accelerated - installation


This tutorialk is about setting up Wan2GP to be fully accelerated.

You can check the accelerators of your current setup by starting Wan2GP and opening the drop-down box in: `Configuration->General->Attention Type`

You will see a big `(NOT INSTALLED)` on all entries that are not present in your setup.




## Pre-Requisites

### Wan2GPp repository

open a terminal in your Wan2GP project. Either an existing project or download it from the repo.

For this example we will assume you are installing from scratch.

```
git clone https://github.com/deepbeepmeep/Wan2GP
cd Wan2GP
```

If you already have an installation of Wan2GP you can continue from this point on and just re-use it. 

all you need is to create a new virtual environment.

### acceleritor lite 

Download the acceleritor lite file from this repository: `acceleritor_lite_python312torch271cu129.txt`
and place it in the Wan2GP folder. We will need it later.




**Create a python virtual environment and activate it** 

we will create a new virtual environment to have things clean and tidy. You can delete your old environment and use this one from now on. 


task       |  Windows                  | Linux
---        |  ---                      | ---
create venv|`py -3.12 -m venv .env_win`|`python3.12 -m venv .env_lin`
activate it|`.env_win\Scripts\activate`|`. ./.env_lin/bin/activate`


At this point you should see at the left of your prompt the name of your environment (e.g. `(.env_win)`)


**Install the acceleritor file**

```
pip install -r acceleritor_lite_python312torch271cu129.txt
```

**now install the project libraries**

```
pip install -r requirements.txt
```

now just start the app as usual 

```
python wgp.py
```
and check that the accelerators were recognized in: `Configuration->General->Attention Type`


