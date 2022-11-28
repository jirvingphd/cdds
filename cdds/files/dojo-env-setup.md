# dojo-env-setup instructions

- The instructions are split into 3 parts:
	- "PART 1: INSTALLATION INSTRUCTIONS (DETAILED)"
	- "PART 2: SUMMARY INSTRUCTIONS"
	- "PART 3: TROUBLESHOOTING"

___

## **PART 1: INSTALLATION INSTRUCTIONS (DETAILED)**

### I. Install GitHub Desktop: https://desktop.github.com/
- Open and log into git account.
	- Install git, if asked.
	
### II. Install a Python Distribution:
- **For Mac's with an Apple Chip:** use [miniforge](https://github.com/conda-forge/miniforge).

	- You will need to enter several commands into the Terminal app to install miniforge.
		- For both steps below, you may need to download several components, including:
			- You may need to run `xcode-select --install` and Agree to the license.
	- ***YOU SHOULD UNINSTALL ANACONDA IF YOU'VE PREVIOUSLY UNINSTALLED IT USING THE LINKED INSTRUCTIONS: https://docs.anaconda.com/anaconda/install/uninstall/***
	- 1. Install [homebrew](https://brew.sh/) by entering the following command into the Terminal app.
	```/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"```

	- 2. Install minforge with homebrew by entering the following command into the terminal app:
	```brew install miniforge```
	
	- 3. May need to run 
	```conda init zsh```

		
- **For Windows, Macs with an Intel chip, and Linux:** use [Anaconda](https://www.anaconda.com).
	- Navigate to https://www.anaconda.com/products/distribution  and download and install Anaconda.

### III. Clone dojo-env-setup repo
- Clone the dojo-env-setup repo using GitHub Desktop or the terminal command:  https://github.com/coding-dojo-data-science/dojo-env-setup

- Method A) Using GithubDesktop:
	- Navigate to repo's website, make sure you're logged into GitHub in your browser, and then click green `Code` button and select `Open in GitHub Desktop`
	- Save to local folder and Use the `Repository` menu to Open in GitBash/Terminal
- Method B) Using Shell Commands:
	- Enter the following command in GitBash (on Windows) or Terminal (on Mac)
	```bash
	git clone https://github.com/coding-dojo-data-science/dojo-env-setup
	cd dojo-env-setup
	``` 
	

### IV. Build the dojo-env environemnt using the correct command for your os from the options below:
```python
## Env Creation Commands by OS
# Windows 
conda env create -f environment_windows.yml

# Mac - Intel Processor 
conda env create -f environment_mac_intel.yml

# Mac - Apple Chip 
conda env create -f environment_mac_mchip.yml
```
- Wait patiently for the process to finish.

### V. Activate dojo-env and set it as the default Python environment:
- For Windows computers:
	- enter the following command in your Terminal/GitBash: 
	```bash
	source activate dojo-env
	python -m ipykernel install --user --name dojo-env --display-name "Python (dojo-env)"
	touch $HOME/.bash_profile
	echo "source activate dojo-env" >> $HOME/.bash_profile
	echo 'alias jnb="jupyter notebook"' >> $HOME/.bash_profile
	source ~/.bash_profile
	```
	
- For Mac computers:
	- enter the following command in your Terminal: 
	```bash
	conda activate dojo-env
	python -m ipykernel install --user --name dojo-env --display-name "Python (dojo-env)"
	touch $HOME/.zshrc
	echo "source activate dojo-env" >> $HOME/.zshrc
	echo 'alias jnb="jupyter notebook"' >> $HOME/.zshrc
	source ~/.zshrc
	```


___

## PART 2) SUMMARY INSTRUCTIONS

### Summary of MacOS (With Apple Chip) Instructions:
- Install GitHub Desktop & Git: https://desktop.github.com/
- Install base Python (homebrew & miniforge):
	```bash
	/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
	
	brew install miniforge
	conda init zsh
	```
- Clone and create dojo-env from repo:
	```bash
	git clone https://github.com/coding-dojo-data-science/dojo-env-setup
	cd dojo-env-setup

	conda env create -f environment_mac_mchip.yml
	```

- Activate dojo-env, install kernel, and set dojo-env to default:
	```bash
	conda activate dojo-env
	python -m ipykernel install --user --name dojo-env --display-name "Python (dojo-env)"
	
	touch $HOME/.zshrc
	echo "conda activate dojo-env" >> $HOME/.zshrc
	echo 'alias jnb="jupyter notebook"' >> $HOME/.zshrc
	
	source $HOME/.zshrc
	```

### Summary of MacOS (With Intel Processor) Instructions

- Install GitHub Desktop & Git: https://desktop.github.com/
- Install Base Python (Anaconda): https://www.anaconda.com/products/distribution

- Clone and create dojo-env from repo:
	```bash
	git clone https://github.com/coding-dojo-data-science/dojo-env-setup
	cd dojo-env-setup
	
	conda env create -f environment_mac_intel.yml
	```
	
- Activate dojo-env, install kernel, and set dojo-env to default:
	```bash
	conda activate dojo-env
	python -m ipykernel install --user --name dojo-env --display-name "Python (dojo-env)"
	
	touch $HOME/.zshrc
	echo "conda activate dojo-env" >> $HOME/.zshrc
	echo 'alias jnb="jupyter notebook"' >> $HOME/.zshrc
	
	source $HOME/.zshrc
	```

### Summary of Windows Instructions
- Install GitHub Desktop & Git: https://desktop.github.com/
- Install Base Python (Anaconda): https://www.anaconda.com/products/distribution

- Clone and create dojo-env from repo:
	```bash
	git clone https://github.com/coding-dojo-data-science/dojo-env-setup
	cd dojo-env-setup
	
	conda env create -f environment_windows.yml
	```
	
- Activate dojo-env, install kernel, and set dojo-env to default:
	```bash
	source activate dojo-env
	python -m ipykernel install --user --name dojo-env --display-name "Python (dojo-env)"
	
	touch $HOME/.bash_profile
	echo "source activate dojo-env" >> $HOME/.bash_profile
	echo 'alias jnb="jupyter notebook"' >> $HOME/.bash_profile
	
	source ~/.bash_profile
	```
	
___ 


## Troubleshooting


### Reinstalling dojo-env
- Open Terminal/GitBash 
- Run the following commands to deactivate & remove the dojo-env (note: does not remove Anaconda/miniforge):

	- For Windows:
		```bash
		source activate base
		conda remove --name dojo-env --all
		y
		```

	- For Macs:
		```bash
		conda activate base
		conda remove --name dojo-env --all
		y
		```