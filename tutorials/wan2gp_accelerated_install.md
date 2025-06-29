#WAN2GP accelerated installation


We will use Wan2GP as an example on how to leverage this project to accelerate a project.

**Clone Project**

```
git clone https://github.com/deepbeepmeep/Wan2GP
cd Wan2GP
```


**Create a python virtual environment and activate it** 

task       |  Windows                  | Linux/Mac
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