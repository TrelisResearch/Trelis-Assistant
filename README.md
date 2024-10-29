# Trelis-Assistant
A Coding Assistant for Jupyter Labs

## Getting Started
Trelis Assistant supports Jupyter Lab 4 and above, simply:
1. `pip install trelis`
2. Refresh the page and click on the "Trelis" button in the left toolbar.
3. Follow the link to get an API key.

**Troubleshooting OR running in a remote/hosted environment:**
- You'll need to have installed yarn and node.
- You can do this using this code snippet in a Jupyter Lab cell:
```
import os
import subprocess

def check_node_yarn():
    # Check if Node.js is installed
    try:
        node_version = subprocess.check_output(["node", "--version"]).decode().strip()
        print(f"Node.js is installed: {node_version}")
    except FileNotFoundError:
        print("Node.js is not installed.")
        install_node()

    # Check if Yarn is installed
    try:
        yarn_version = subprocess.check_output(["yarn", "--version"]).decode().strip()
        print(f"Yarn is installed: {yarn_version}")
    except FileNotFoundError:
        print("Yarn is not installed.")
        install_yarn()

def install_node():
    print("Installing Node.js...")
    # Download Node.js binary (you can change the version if needed)
    os.system("curl -O https://nodejs.org/dist/v22.6.0/node-v22.6.0-linux-x64.tar.xz --silent")
    
    # Extract Node.js
    os.system("tar -xf node-v22.6.0-linux-x64.tar.xz --no-same-owner")
    
    # Add Node.js to the PATH for the current notebook session
    node_bin_path = os.path.abspath("node-v22.6.0-linux-x64/bin")
    os.environ['PATH'] = node_bin_path + ":" + os.environ['PATH']
    print(f"Node.js installed to {node_bin_path}")

    # Verify installation
    node_version = subprocess.check_output(["node", "--version"]).decode().strip()
    print(f"Node.js version: {node_version}")

def install_yarn():
    print("Installing Yarn...")
    # Install Yarn via script
    os.system("curl -o- -L https://yarnpkg.com/install.sh | bash")
    
    # Add Yarn to the PATH for the current notebook session
    yarn_bin_path = os.path.expanduser("~/.yarn/bin")
    os.environ['PATH'] = yarn_bin_path + ":" + os.environ['PATH']
    print(f"Yarn installed to {yarn_bin_path}")

    # Verify installation
    yarn_version = subprocess.check_output(["yarn", "--version"]).decode().strip()
    print(f"Yarn version: {yarn_version}")

# Run the check and installation process
check_node_yarn()
```
## FAQ

- **What language models do you use?**  
  Trelis Assistant uses Google Gemini models.

- **Is my data used for training?**  
  Trelis does not store or use user data for training AI models.

- **Does this work with Jupyter Notebook, Colab, or Kaggle?**  
  Currently, Trelis Assistant supports Jupyter Lab 4 and above only. Support for Jupyter Notebook, Colab, or Kaggle is not yet available.
