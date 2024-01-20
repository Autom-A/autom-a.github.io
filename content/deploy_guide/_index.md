+++
archetype = "chapter"
title = "3. Deploy Guide"
weight = 3
+++

Here you will find the steps for installing AutomA on your information system. Before explaining these steps, we would like to present a few aspects of AutomA that have an impact on its installation. AutomA is :
- **Offline**: AutomA is designed to operate without an Internet connection, so it is possible to deploy our software on all your information systems.
- **Agentless**: AutomA uses Ansible to run, so no agents are installed on your machines. All you need is your administration machine.
- **Exportable**: AutomA allows you to export your configurations for application on other information systems. For example, AutomA can be installed on a machine with Internet access to take advantage of the latest updates while deploying configurations on other information systems.

## Manual Installation

### Step 1 - Prerequisites

The list of software required to install AutomA :
- git
- python3 (>3.9)
- pip3
- an up-to-date web browser

### Step 2 - Downloading the repository

Using git, clone the repository:
```bash
git clone https://github.com/Autom-A/AutomA-WebUI.git
```

Once this has been done, you need to download the playbooks:
```bash
cd AutomA-WebUI
git submodule update --init --recursive 
```

### Step 3 - Downloading dependencies

The project needs some python3 dependencies:
- ansible-runner
- Flask
- flask-core
- jinja2
- pyyaml

To download them, run the following command:
```bash
pip3 install -r requirements.txt
```

### Etape 4 - Run the project

Simply run the following command:
```bash
python3 src/main.py
```

Then open your navigator and type in address bar `http://localhost:9123` (with default config).
