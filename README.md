# CrossOS Acceleritor - AI accelerited!


The "k-lite codec pack" for AI...

remember back then when you had to install this and that codec to watch a video? then the codec-packs came along and all problems were solved?

now, we sweat looking for AI acclerator libraries to try that one project that just appeared: Flashattention, Sageattention, Mamba... and the few guides we find are all like "yeh, but this works only on linux", "you have to compile yourself", "you need to hack your system like this...".. 

well... here you will find every last one of these precious libraries... everyone? yes.. **E-V-REY-OONEE!!** (*im trying...*)

The project is universal and will work virtually on anything! as long as your target project supports the accelerator!

You can take this project and apply it to any AI project you want! speedup: ComfyUI, Framepack, TTS, Bagel, wanGP... pretty much anything that runs on python.

### Features 
This setup will:

- Give you access to all possible acceleritor libraries:
    - Currently: xFormers, triton, flashattention2, Sageattention, CausalConv1d, MambaSSM
    - more coming up! so stay tuned
- Fully CUDA accelerated (sorry no AMD or Mac at the moment!)
- One pit stop for acceleration:
    - All accelerators are custom compiled and tested by me and work on ALL modern CUDA cards: 30xx(Ampere), 40xx(Lovelace), 50xx (Blackwell).
    - works on Windows and Linux. Compatible with MacOS.
    - the installation instructions are Cross-OS!: if you learn the losCrossos-way, you will be able to apply your knowledge on Linux, Windows and MacOS when you switch systems... aint that neat, huh, HUH??
- get the latest versions! the libraries are compiled on the latest official versions.
- Get exclusive versions: some libraries were bugfixed by myself to work at all on windows or on blackwell.
- All libraries are compiled on the same code base by me to they all are tuned perfectly to each other!
- For project developers: you can use these files to setup your project knowing MacOS, Windows and MacOS users will have the latest version of the accelerators.

what is currently **NOT supported**:
- Any other GPU than Nvidia (AMD, Intel, etc) as these accelerators are nvidia only or the most part.
- NVidia 10xx and 20xx and older... sorry guys :( the accelerators do not support you in the new versions.

# Usage

The `acceleritor*.txt` files in this project are crafted to contain full sets of accelerator libraries that integrate well with each other. You can use the files in this manners:
- as a whole by installing them in your desired project
- using them to get only what you need for your requirements.txt: open the file and only use the libraries you need by copying the line blocks of each library. You need to respect the dependencies of the libraries: e.g. Sage Attention has this comment: `#Needs Pytorch, Triton`. this means you need to copy the Pytorch code block and the Triton code block into your requirements.txt.



## Pre-Requisites


- Only Python3.12 is currently supported. More coming up.
- RTX CUDA card 30xx, 40xx or 50xx
- Your PC should be setup for AI. Check next chapter to see if you already fulfill it.

### Manual AI Setup

At least you will need:

- you need python 3.12 installed. not conda python but the real python. 
- On windows:
    - MSVC with VCTools, WindowsSDK11 and CMake enabled.
    - ideally: developer mode enabled
- On Linux: you should cmake, g++ and development headers installed.


### Automated AI-Setup


If you want an automated and efficient way to setup a software development environment for AI and Python, you can use my other project: CrossOS_Setup, which setups your PC (Mac, Windows or Linux) automatically to a full fledged AI Software Development station. It includes a system-checker to assess how well installed your current setup is, before you install anything:

https://github.com/loscrossos/crossos_setup

Thats what i use for all my development across all my systems. Its also fully free and open source. No strings attached!



## The right file

first of all you will need to select the right file. You should know these parameters to use this effectively:

- **Python version**: The most important parameter is your python version. You can safely use python3.12. The file sets the basis for your installation. 
- **Pytorch**: For compatibility we set it up with Pytorch 2.7.1: its the current stable version and supports all major RTX cards 3, 4 and 5 series.
- **CUDA**: Since CUDA is backwards compatible, the libraries are compiled with the current latest version 12.9.

The file is named after these parameters:

    acceleritor_full_python312torch271cu129

- `acceleritor`: the name of the project
- `full`: contains all libraries. the "`lite`" version contains a selection of the most common libraries used (xFormers, Triton, Flash-attention, SageAttention).
- `python312`: this file is compatible with python 3.12. This must match your virtual environment.
- `torch271`: This set was built on PyTorch 2.7.1. This should match your libraries.
- `cu129`: This set was built using CUDA 12.9. Since CUDA is forwards and Backwards compatible with "major versions", you should be using CUDA 12.x.


## Installation

The installation is easy: just install your project as you normally would, but before installing requirements.txt install the acceleritor file and remove references to torch on the requirements.txt. 

Basically the procedure is as follows to accelerite any project:

1. Clone your project
2. create a venv and activate it.
3. if existent: remove any references to torch/torchvision/Torchaudio from the existing requirement.txt
4. install the acceleritor file
5. install the remaining requirements from your project
6. profit???



## Installation Examples

[Wan2GP Installation](tutorials/wan2gp_accelerated_install.md)

enjoy!



## Want to help?

Feel free to contribute with installation guides in the issues section for projects that you accelerated with Acceleritor! I will can integrate them in the tutorial section.



## Known issues

**Windows xFormers v0.0.31**

as of 29JUN2025 the current xFormers version 0.0.31 has a bug on windows. you can fix it by issuing these commands once from the "Wan2GP" installation folder above.

```
ren ".env_win\Lib\site-packages\xformers\pyd" "_C.pyd"
ren ".env_win\Lib\site-packages\xformers\flash_attn_3\pyd" "_C.pyd"
```

if you get no error or any message at all then it worked.




# Troubleshooting

- Sage-Attention: For people who might be getting the error: with tcc and includes in the logs: They are missing the python headers.
 - you need to install python 3.12 on your system (not from conda!)
 - alternatively you can get the headers and copy them in the venv then it should work fine. you can take it from the main python 312 install. installing as described above should suffice.


- if you have problems post an issue with as much of the console errors as possible, your system info (OS, Python versiom, Pytorch version, target Project) and ideally an example workflow so i can reproduce the error. will do my best to help




# Roadmap

- ✅ xFormers
- ✅ triton
- ✅ flashattention2
- ✅ Sageattention
- ✅ CausalConv1d
- ✅ MambaSSM
- Another Python version
- Coming up: Deepspeed
- Coming up: FlashAttention3


feel free to propose any library you find difficult to find or get to run.. if there is enough "public interest" i will take a look.