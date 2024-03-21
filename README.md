# AnyGPT-on-Colab---OLLAMA-with-UI-on-Colab
Google Colab Notebook describes step by step how to run Ollama with UI on Colab and expose the created user interface to the internet- guide described in the following article:
https://medium.com/@bartek.lewicz/launch-your-own-chatgpt-clone-for-free-on-colab-shareable-and-online-in-less-than-10-minutes-da19e44be5eb

Requirements:

Google Account
 Google Colab (See Part 1 of the referenced article for getting started with Colab)
 
Process:

Install Ollama:

Run the following code block in your Colab notebook:

Bash
# Pull Ollama install script and execute
!curl -fsSL https://ollama.com/install.sh | sh
# Run Ollama service in the background
!sudo ollama serve &>/dev/null&
Use code with caution.
Update Node.js:

Download and install the latest Node.js version:

Bash
# Download the install script for the current Node.js version and run it.
!curl -fsSL https://deb.nodesource.com/setup_current.x | sh
# Update the system's package index.
!sudo apt-get update
# Install new Node.js version.
!sudo apt-get install -y nodejs
Use code with caution.
Download and Run UI:

Clone the Jakob Hoeg Mørk's NextJS Ollama LLM UI from GitHub:

Bash
# Clone the repository from GitHub.
!git clone https://github.com/jakobhoeg/nextjs-ollama-llm-ui
# Change directory to the downloaded project directory
%cd nextjs-ollama-llm-ui
# Rename example.env file to .env to be used as our default configuration
!mv .example.env .env
# Install dependencies using Node Package Manager
!npm install
# Start the web server, discard all outputs and run in the background.
!npm run dev &>/dev/null&
Use code with caution.
Find Colab Instance IP Address:

Run the following code block to get your Colab instance's public IP address:

Bash
# Retrieve Public IP address of Google Colab's instance.
!curl ifconfig.me
Use code with caution.
Install Localtunnel and Expose UI:

Install Localtunnel:

Bash
!npm install localtunnel
Use code with caution.
Start Localtunnel and expose port 3000 (UI port) to the internet:

Bash
!npx localtunnel --port 3000
Use code with caution.
This will provide you with a URL to access your UI.
Access Ollama UI and Download Models:

Open the provided URL in your browser.
Enter the public IP address obtained in step 4 as the Tunnel Password on the first visit.
Select "pull model" from the menu and choose a model from the Ollama Model Library (https://ollama.com/library).
Downloading the model might take 2-3 minutes. Refresh the page or select "New chat" after download.
Complete Code:

Refer to the Google Colab notebook on GitHub: [invalid URL removed].
Considerations:

Google Colab free tier limitations:
12-hour notebook runtime and 2 simultaneous sessions.
T4 GPU access might be limited during peak hours.
CPU usage leads to slower response times.
80-100GB storage, but large models might exceed RAM/VRAM.
This approach is for experimental and development purposes only, not suitable for production environments.
Additional Resources:

NextJS-Ollama-LLM-UI GitHub: https://github.com/jakobhoeg/nextjs-ollama-llm-ui
Localtunnel GitHub: https://github.com/localtunnel
Ollama Homepage: https://ollama.com/
