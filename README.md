# Fork
## Reason for fork
The purpose of this fork is to further the showcasing ability of the chile2010a and b file to better observe the effect that the change that the Manning's n value has on (a basic simulation of) a tsunami.

## Changes made in this fork
This fork has made changes to the /notebooks/geoclaw directory. There are changes in both the Chile2010a and Chile2010b directories. In each, there is the addition of an installation_guide.md file, a setrun_alt.py file, and the gauge32412-actual-detide.png file - modified from the dart32412_comp-2.png file in /clawpack_src/clawpack-$CLAW_VERSION/geoclaw/examples/tsunami/chile2010


## Installation

If the following are not already installed:

- Install [pip](https://pip.pypa.io/en/stable/installing) (if not already installed).

- Install [gfortran](https://gcc.gnu.org/wiki/GFortranBinaries) (You can use a different fortran compiler, but change the parts which mention 'gfortran' to the name of your fortran compiler).

Enter the following commands into the terminal:

#-----------------------------------------------------------------------------------------------

export CLAW_VERSION=v5.7.0  # used several places in next commands

pip install --src=$HOME/clawpack_src --user -e git+https://github.com/clawpack/clawpack.git@$CLAW_VERSION#egg=clawpack-$CLAW_VERSION

git clone https://github.com/clawitzer/apps.git $HOME/clawpack_src/clawpack-$CLAW_VERSION/apps # Install clawitzer/apps to $HOME/clawpack_src/clawpack-$CLAW_VERSION/apps

echo 'export CLAW=$HOME/clawpack_src/clawpack-$CLAW_VERSION export FC=gfortran' | sudo tee -a '$HOME/.bashrc' # Write environment variables CLAW and FC to .bashrc config file

#You may need to enter the next command seperately, as the previous command may require a password to initiate change.

echo 'export CLAW=$HOME/clawpack_src/clawpack-$CLAW_VERSION export FC=gfortran' | sudo tee -a '$HOME/.profile' # Write environment variables CLAW and FC to .profile config file

#-----------------------------------------------------------------------------------------------

Now reboot your machine to allow machine and python to read new environment variables


## How to use
Simply run the chile2010x_alt.ipynb. If you followed the above Installation section, please contact me if you've had issues. If you encounter problems, and have followed the CLAWPACK installation guide as given [here](https://www.clawpack.org/installing.html#pip-install); first ensure you have installed the version of CLAWPACK this notebook requires, then either check out the installation_guide.md file - which documents solutions to the issues I encountered during installation - or follow the Installation section above or . Please note that in the Makefile of the Chile2010a and b directories, I have inserted the flag detailed in the installation_guide.md, shown in problem titled 'Type mismatch - fortran'. If you encounter an error with a Makefile, please take off the flag and re-run. If this does not solve your issue, I suggest you search online. 

### Notes
- This is my first repository on github, and I am really using this as a quick means to an end to show people who need to view my work. Thus, I do not intend to become familiar with and adhere to good practices of maintaining a repository. Therefore please do not take this to be anything other than a fork for my own personal use, but that if you wish to use, you are more than welcome to. 
- When I write chile2010x, the x represents either the 'a' or 'b' version. There is no actual file called chile2010x.ipynb, or chile2010x_alt.ipynb.
- Since this is a work in progress, the markdown blocks in the chile2010x_alt.ipynb may have less detail than desired. They contain descriptions I feel are pertinent to the program, but if you are looking for more detail - I recommend first going through the chile2010x.ipynb file, as this is the original CLAWPACK version, and then move to mine to observe the changes I've made.

