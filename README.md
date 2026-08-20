# Conda Environment Setup & Practice Guide for the CRABS 2026 Connectomics workshop

This guide provides step-by-step instructions for installing Conda (via Miniforge), setting up an environment from a provided YAML file, configuring JupyterLab, and launching a notebook for hands-on practice. It includes instructions for Linux, macOS, and Windows users.

---

## 1. Install Miniforge (Recommended Conda Distribution)

[Miniforge](https://github.com/conda-forge/miniforge) is the community-driven, minimal installer for Conda that defaults to the `conda-forge` channel. It is lightweight, fast, and does not require a paid license for commercial use.

### Windows
1. Download the latest Miniforge Windows installer from the official repository: [Miniforge3-Windows-x86_64.exe](https://github.com/conda-forge/miniforge/releases/latest/download/Miniforge3-Windows-x86_64.exe).
2. Double-click the downloaded `.exe` file to run the installer.
3. Follow the prompts. When asked, it is highly recommended **not** to add Conda to your system PATH. Instead, use the "Miniforge Prompt" that will be added to your Start Menu.
4. Open the **Miniforge Prompt** from your Start menu to continue.

### macOS
The easiest way to install Miniforge on a Mac is using Homebrew. If you don't have Homebrew, you can use the bash installer.

**Option A: Using Homebrew (Recommended)**
Open your terminal and run:
```bash
brew install miniforge
```

**Option B: Using the Bash Installer**
Open your terminal and run:
```bash
curl -L -O "https://github.com/conda-forge/miniforge/releases/latest/download/Miniforge3-MacOSX-$(uname -m).sh"
bash Miniforge3-MacOSX-$(uname -m).sh
```
Follow the prompts. Press `Enter` to scroll through the terms, type `yes` to agree, and type `yes` when asked to initialize Conda. Restart your terminal afterward.

### Linux
Open your terminal and run the following commands to download and execute the installer:
```bash
wget "https://github.com/conda-forge/miniforge/releases/latest/download/Miniforge3-Linux-$(uname -m).sh"
bash Miniforge3-Linux-$(uname -m).sh
```
Follow the on-screen prompts. Agree to the license and let the installer initialize Miniforge by answering `yes` at the end. Restart your terminal for the changes to take effect.

---

## 2. Create the Environment from `environment.yml`

Once Miniforge is installed and your terminal (or Miniforge Prompt) is open, navigate to the directory containing your project's `environment.yml` file.

1. **Navigate to your project directory:**
   ```bash
   cd path/to/your/project
   ```

2. **Create the environment:**
   Miniforge includes `mamba` (a faster C++ reimplementation of conda) by default, which speeds up package solving and installation.
   ```bash
   mamba env create -f environment.yml
   ```
   *(Note: You can also use `conda env create -f environment.yml` if you prefer).*

3. **Activate the environment:**
   Look at the top of your `environment.yml` file to find the environment name (e.g., `name: my-env`). Activate it using:
   ```bash
   conda activate CRABS_2026_connectomics
   ```

---


## 3. Create a Jupyter Kernel for Your Environment

To ensure JupyterLab can find and use the specific packages installed in your newly created environment, you must register the environment as a Jupyter kernel.

With your environment still activated, run:
```bash
python -m ipykernel install --user --name CRABS_2026_connectomics
```

---

## 5. Launch JupyterLab and Open a Notebook

You are now ready to start your hands-on practice.

1. **Launch JupyterLab:**
   In your terminal, while in your project directory, run:
   ```bash
   jupyter lab
   ```
   This will start the Jupyter server and automatically open the JupyterLab interface in your default web browser. (If it doesn't open automatically, copy and paste the `http://localhost:8888/...` URL shown in your terminal into your browser).

2. **Create or Open a Notebook:**
   - **To open an existing notebook:** Use the file browser on the left sidebar of JupyterLab to locate and double-click your `.ipynb` file.
   - **To create a new notebook:** In the "Launcher" tab, look under the "Notebook" section and click on the button labeled with your custom display name (e.g., **Python (\<environment_name\>)**).

3. **Verify the Kernel:**
   In the top right corner of your open notebook, ensure it displays the name of your custom kernel (`CRABS_2026_connectomics`). If it shows a different kernel, click on the name and select yours from the dropdown menu.

You are now fully set up to write, run, and experiment with code for the workshop!
