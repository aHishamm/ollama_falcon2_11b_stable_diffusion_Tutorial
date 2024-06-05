# ollama_falcon2_11b_stable_diffusion_Tutorial
This repository contains the necessary steps for installing ollama and running TII's Falcon 11b in 4-bit quantization, along with Whisper for ASR, and ComfyUI for handling the stable diffusion backend

### Preview of the system 
- Insert a video of the it working here 


### Project Prequisites 
1. Node and NPM need to be installed 
2. Conda or venv (optional) (Conda was used in this tutorial)
3. Ollama (To download the 4-bit quantized Falcon 11B model)
4. Local Whisper for Speech-to-text generation (STT)
5. Open WebUI 
6. ComfyUI for managing the stable diffusion pipeline
7. RealisticVisionV60B1 as the base model for the diffusion pipeline (optional) (Download any pretrained model checkpoint that you would like and use here)

### Steps for installation
#### Installing Node and NPM 
The below steps are for installing node and npm on MacOS:
```bash
# installs nvm (Node Version Manager)
curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.39.7/install.sh | bash
# download and install Node.js
nvm install 20
# verifies the right Node.js version is in the environment
node -v # should print `v20.14.0`
# verifies the right NPM version is in the environment
npm -v # should print `10.7.0`
```
#### Creating an Anaconda environment and installing the required dependencies
Create an environment and install the required dependencies by running the commands below: 
```bash
#Creating an environment called locallm with python 3.11 installed
conda create -n locallm python=3.11
#Activating the environment
conda activate locallm
#Installing the required libraries and packages (Install the packages listed in the attached requirements.txt file)
pip install -r requirements.txt
```
#### Installing Ollama 
Download and install Ollama from the link below:        
https://www.ollama.com/
#### Installing Local Whisper 
To install Whisper locally on your machine run the following pip command to install the latest commit from OpenAI's repository: 
```bash
pip install git+https://github.com/openai/whisper.git 
```
Whisper requires ffmpeg to be installed locally: 
```bash
# on Ubuntu or Debian
sudo apt update && sudo apt install ffmpeg
# on Arch Linux
sudo pacman -S ffmpeg
# on MacOS using Homebrew (https://brew.sh/)
brew install ffmpeg
# on Windows using Chocolatey (https://chocolatey.org/)
choco install ffmpeg
# on Windows using Scoop (https://scoop.sh/)
scoop install ffmpeg
```
#### Installing Open WebUI 
To build and install Open WebUI locally, run the following commands: 
```bash
git clone https://github.com/open-webui/open-webui.git
cd open-webui/
# Copying required .env file
cp -RPp .env.example .env
# Building Frontend Using Node
npm install
npm run build
# Serving Frontend with the Backend
cd ./backend
pip install -r requirements.txt -U
bash start.sh
```
This will run the the ```start.sh``` shell script on the current terminal/shell window, it is advised to run it in a detached terminal session or in a containerized form. 
#### Downloading the RealisticVisionV60B1 base model 
Download the pruned model safetensors from CivitAI or HuggingFace: https://civitai.com/models/4201/realistic-vision-v60-b1
#### Downloading and running ComfyUI
- git clone the ComfyUI repository https://github.com/comfyanonymous/ComfyUI.git          
- navigate to the models/checkpoints folder inside the cloned repository, and paste the aforementioned downloaded model there. 
- Launch comfyUI by running ```python main.py```
