# Fork
## Reason for fork
The purpose of this fork is to showcase the effect that the change that the Manning's n value has on a tsunami.

## Changes made in this fork
This fork has made changes to the /notebooks/geoclaw directory. There are changes in both the Chile2010a and Chile2010b directories. In each, there is the addition of a setrun_alt.py file, and a chile2010x_alt.ipynb file.


## Installation

If the following are not already installed:

- Install pip (if not already installed).

- Install gfortran (You can use a different fortran compiler, but change the parts which mention 'gfortran' to the name of your fortran compiler).

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
Simply run the chile2010x_alt.ipynb. If you encounter problems, and have followed the CLAWPACK installation guide as given [here](https://www.clawpack.org/installing.html#pip-install), check out the installation_guide.md file, which documents solutions to the issues I encountered during installation, and running the examples I am working with. Please note that in the Makefile of the Chile2010a and b directories, I have inserted the flag detailed in the installation_guide.md, shown in problem titled 'Type mismatch - fortran'. If you encounter an error with a Makefile, please take off the flag and re-run. If this does not solve your issue, I suggest you search online. 

### Notes
- This is my first repository on github, and I am really using this as a quick means to an end to show people who need to view my work. Thus, I do not intend to become familiar with and adhere to good practices of maintaining a repository. Therefore please do not take this to be anything other than a fork for my own personal use, but that if you wish to use, you are more than welcome to. 
- When I write chile2010x, the x represents either the 'a' or 'b' version. There is no actual file called chile2010x.ipynb, or chile2010x_alt.ipynb.
- Since this is a work in progress, I do not advise following the markdown blocks in the chile2010x_alt.ipynb to rigourously, as they contain small descriptions I have added, but there is a chance the original md blocks may be misplaced or missing where they otherwise should be. If you are looking at this file to learn about this simulation, I recommend first going through the chile2010x.ipynb file, as this is the original CLAWPACK version, and then move to mine to observe the changes I've made.

---
# Clawpack Applications Repository

This is a repository of applications of Clawpack and related software.  Many of these examples are maintained as full-fledged examples that would be too large and/or complex to include in the individual repository examples.  Also note that some of the applications are also maintained by people outside of the Clawpack developer team so questions should directed appropriately.

### Application Submodules
Some of the applications are included as git submodules of the main repository.  This allows the responsible developers to maintain their application independent of the rest of the apps repository and lets users checkout only those apps that they are interested in.  If you have already cloned the `apps` repository, then to fetch all submodules you can do the following:
```
$> cd $CLAW/apps  # or proper path to apps
$> git submodule init
$> git submodule update
```

The file `.gitmodules` contains a list of the submodules that will be fetched.  Refer to the `git submodule` documentation for instructions on checking out only one submodule.

If you have not yet cloned the `apps` repository, you can clone it along with all the submodules via the following (with a new enough version of `git`):
```
$> cd $CLAW  # or where ever you want apps to be
$> git clone --recursive https://github.com/clawpack/apps
```

