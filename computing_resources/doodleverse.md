Under construction :)

# Overview

Optional: Watch videos in this [crash course](https://developers.google.com/machine-learning/crash-course)

Optional: Step through [this Colab notebook](https://colab.research.google.com/drive/1NBfpdD9AcDTvvnXroPtBrsTQqRGS4M6r?usp=sharing) written by Dan Buscombe (updated by Joanmarie for tensorflow v 2.15) 

# Choosing a platform/OS

As stated in the Doodleverse docs, the software is intended to run on <b>Windows or Linux</b>. Recall that you have options: 
1. Running the software <b>locally on your own laptop</b>. You can install Anaconda, miniconda, or any Python accessor of your choice, and it can run through a terminal instance in JuptyerLab in Anaconda, VS Code, or simply a command line interface. If you have Windows, you can install [Windows Subsystem for Linux](https://learn.microsoft.com/en-us/windows/wsl/install) WSL, which you can then once again run with the command line or [use WSL as your enviroment in VS Code](https://learn.microsoft.com/en-us/windows/wsl/tutorials/wsl-vscode). Or, you can run a lot of code in Windows, but be aware that some other software is not developed for Windows (Linux is practically universal).

2. Running the software on the <b>Big Rig</b> (which can be connected to remotely from your own laptop). You can follow the steps described above to install WSL and VS Code to work on Linux on the Big Rig. 

3. Running the software on the </b>HPC cluster</b>. Note that a major technical hurdle is that the cluster (1) cannot open a proxy server (and thus you need to create an ssh tunnel to run Doodler) and (2) does not have a display enabled to run Segmentation Gym scripts that use the `TKinter` package that trigger dialog boxes (the Doodleverse developers have since created a `no_tkinter` version of their scripts to solve this for us). 

# Creating image-label pairs

## Doodler on sciclone

1. Log into your cluster node of choice as you usually do, install Dash Doodler if you haven't already, and activate your `dashdoodler` environment. 
2. Run `python doodler.py` after navigating to the directory with `cd dash_doodler`
3. Make an ssh tunnel to copy and paste the address that Doodler spits out. Note the address: it should be http://127.0.0.1:8050/  The server is 127.0.0.1 and the port is 8050. 
4. Open another Terminal. Do `ssh` like you normally would but add flags `-NfL` (note capitals). The general syntax for ssh tunneling is:

`ssh -NfL [port]:[server]:[port] [your id]@[linux machine address]`

For example, I would use `ssh -NfL 8050:astral.sciclone.wm.edu:8050 jdelvecchio01@astral.sciclone.wm.edu`

5. You will be prompted for your password; enter it. If nothing happens, it's working!
6. Copy and paste or type the http address into your web browser of choice. It should pop us as Doodler!!

# Training a model

## Build the environment
1. Go to the Segmentation Gym [repo](https://github.com/Doodleverse/segmentation_gym0)
2. Read through everything on the [wiki](https://github.com/Doodleverse/segmentation_gym/wiki) (but maybe hold off on the demo test set)
3. Go through their [test dataset](https://github.com/Doodleverse/segmentation_gym?tab=readme-ov-file#test-dataset) and make sure everything works 