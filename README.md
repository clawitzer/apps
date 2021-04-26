# IMPORTANT!
This project has been moved to [https://gitlab.com/bittern/BotFricTsunami](https://gitlab.com/bittern/BotFricTsunami). Please visit this location for an updated version of this repository.

---

# Fork
## Reason for fork
The purpose of this fork is to further the showcasing ability of the chile2010a and b file to better observe the effect that the change that the Manning's n value has on (a basic simulation of) a tsunami.

## Changes made in this fork
This fork has made changes to the /notebooks/geoclaw directory. There are changes in both the Chile2010a and Chile2010b directories. The main new notebook (to be ran) is [chile2010b_alt.ipynb](https://github.com/see-on/apps/blob/master/notebooks/geoclaw/chile2010b/chile2010b_alt.ipynb) .In each, there is the addition of a [CLAWdoc_install_issues.md](https://github.com/see-on/apps/blob/master/CLAWdoc_install_issues.md) file, and the [gauge32412-actual-detide.png](https://github.com/see-on/apps/blob/master/notebooks/geoclaw/chile2010b/gauge32412-actual-detide.png) file - modified from the dart32412_comp-2.png file in /clawpack_src/clawpack-$CLAW_VERSION/geoclaw/examples/tsunami/chile2010

# Notes
- This is my first repository on github, and I am really using this as a quick means to an end to show people who need to view my work. Thus, I do not intend to become familiar with and adhere to good practices of maintaining a repository. Therefore please do not take this to be anything other than a fork for my own personal use, but that if you wish to use, you are more than welcome to. 
- When I write chile2010x, the x represents either the 'a' or 'b' version. There is no actual file called chile2010x.ipynb, or chile2010x_alt.ipynb.
- Since this is a work in progress, the markdown blocks in the chile2010x_alt.ipynb may have less detail than desired. They contain descriptions I feel are pertinent to the program, but if you are looking for more detail - I recommend first going through the chile2010x.ipynb file, as this is the original CLAWPACK version, and then move to mine to observe the changes I've made.

# Installation

If the following are not already installed:

- Install [pip](https://pip.pypa.io/en/stable/installing) (if not already installed).

- Install [gfortran](https://gcc.gnu.org/wiki/GFortranBinaries) (You can use a different fortran compiler, but change the parts which mention 'gfortran' to the name of your fortran compiler).

- [Install](https://jupyter.org/install) Jupyterlab or classic Jupyter notebook.

If `vim` is not your preferred text editor, insert the name of your chosen editor instead (e.g `vi`, `nano`, etc.). If you are running a different terminal to bash, replace `~/.bashrc` with your shell's alternative (e.g `~/.zshrc` for a zsh-based terminal).

1. Write environment variables: FC, CLAW, CLAW_VERSION; to .profile configuration file.

`$ sudo vim ~/.profile`

Enter the following lines at the bottom of the .profile file:
```
export CLAW_VERSION=v5.7.0 #CLAWPACK version for Clawitzer/apps
export CLAW=$HOME/clawpack_src/clawpack-$CLAW_VERSION #CLAWPACK directory for Clawitzer/apps 
export FC=gfortran #Name of Fortran compiler
```
Save and exit the editor.

2. Write environment variables: FC, CLAW, CLAW_VERSION; to .bashrc configuration file.

`$ sudo vim ~/.bashrc`

Enter the following lines at the bottom of the .bashrc file:

```
export CLAW_VERSION=v5.7.0 #CLAWPACK version for clawitzer/apps
export CLAW=$HOME/clawpack_src/clawpack-$CLAW_VERSION #CLAWPACK directory for Clawitzer/apps 
export FC=gfortran #Name of Fortran compiler
```
Save and exit the editor.

Now reboot your machine to allow machine and python to read new environment variables.

3. Install CLAWPACK, and clawitzer/apps.
```
$ pip install --src=$HOME/clawpack_src --user -e git+https://github.com/clawpack/clawpack.git@$CLAW_VERSION#egg=clawpack-$CLAW_VERSION #Install CLAWPACK to $HOME/clawpack_src/clawpack-$CLAW_VERSION

$ git clone https://github.com/clawitzer/apps.git $HOME/clawpack_src/clawpack-$CLAW_VERSION/apps #Install clawitzer/apps to $HOME/clawpack_src/clawpack-$CLAW_VERSION/apps
```

## How to use
Start either JupyterLab or classic Jupyter notebook via the respective commands:

```
$ jupyter lab
```
or
```
$ jupyter notebook
```

And enter the outputted URL in your browser. Once inside the jupyter software, navigate to chile2010x_alt.ipynb (located in $HOME/clawpack_src/clawpack-$CLAW_VERSION/apps/notebooks/geoclaw/chile2010x), and run the notebook. If you followed the above Installation section, please contact me if you've had issues. If you encounter problems, and have followed the CLAWPACK installation guide as given [here](https://www.clawpack.org/installing.html#pip-install); first ensure you have installed the version of CLAWPACK this notebook requires, then either check out the CLAWdoc_install_issues.md file - which documents solutions to the issues I encountered during installation - or follow the Installation section above. Please note that in the Makefile of the Chile2010a and b directories, I have inserted the flag detailed in the CLAWdoc_install_issues.md file, shown in problem titled 'Type mismatch - fortran'. If you encounter an error with a Makefile, please take off the flag and re-run. If this does not solve your issue, I suggest you search online.

# More information
For more information on the topic, check out the [How_does_Bottom_Friction_affect_Tsunami_waves_.pdf](https://github.com/see-on/apps/blob/master/How_does_Bottom_Friction_affect_Tsunami_waves_.pdf) file for extra details on a poster made about this software, and information about the mathematics - and choices made - behind this model.
