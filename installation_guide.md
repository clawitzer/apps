# Installation environment

To install CLAWPACK (**v5.7.0**) properly, I ran Arch **Linux** and followed the [pip installation]([Installing Clawpack &#8212; Clawpack 5.7.0 documentation](https://www.clawpack.org/installing.html#pip-install)), using the Fortran compiler **Gfortran**, and **Jupyter notebook** for interfacing with code. The username for the machine in this guide is **jack**, so replace this with the username with your machine where necessary. **vim** is used as the text editor in this guide, so replace it with your preferred editor. If you are running a different terminal to **bash**, replace `~/.bashrc` with your shell's alternative (e.g `~/.zshrc)` for a zsh-based terminal.
Even if you are not running the same OS as in this guide, or running an alternative to another program mentioned here, this guide should point you in the right direction for fixes to be made on your device, you will just need to find out how to 'translate' these instructions to the service you are working with.


# During installation

---

## Environment variables

### Location

After running the `pip install` command at:

https://www.clawpack.org/installing.html#pip-install

This is the code block at which we need to adapt the instructions:

```
export CLAW=$HOME/clawpack_src/clawpack-v5.7.0
export FC=gfortran
```

Example where it occurs (**post installation**) :

http://localhost:8888/notebooks/clawpack_src/clawpack-v5.7.0/apps/notebooks/geoclaw/chile2010a/chile2010a.ipynb

At first cell under the section *Compile and run the GeoClaw code*, with contents:

```
nbtools.make_exe(new=True, verbose=True)  # compile xgeoclaw
```

### Description

These commands set the environmental variables *CLAW* and *FC* **temporarily**. Upon restart, they will no longer exist.

Example where it occurs (**post installation**) :

When running cell, output is :

```
Executing shell command:   make new
*** Possible errors, return_code = 2
Done...  Check this file to see output:

compile_output.txt
```

In the `compile_output.txt` file, at the bottom, it reads :

```
Makefile:57: /clawutil/src/Makefile.common: No such file or directory
make: *** No rule to make target '/clawutil/src/Makefile.common'.  Stop.
```

Indeed, on the linux machine `/clawutil/src/Makefile.common` is not a valid location (considering the first `/` is the root of the filesystem).

### Solution

For the following, replace `vim` with your editor of choice. If you are running a different terminal to bash, replace `~/.bashrc` with your shell's alternative (e.g `~/.zshrc)` for a zsh-based terminal.

The commands must be inserted into configuration files to become permanent. Enter the following into a terminal:

`sudo vim ~/.profile`

Insert these commands at the end of the file :

```
export CLAW=$HOME/clawpack_src/clawpack-v5.7.0
export FC=gfortran
```

Save and exit the editor (vim).

`sudo vim ~/.bashrc`

Insert these commands at the end of the file :

```
export CLAW=$HOME/clawpack_src/clawpack-v5.7.0
export FC=gfortran
```

Save and exit the editor (vim).

In the terminal, enter the commands:

```
source ~/.profile
source ~/.bashrc
```

Now the new configuration files should be set on your machine.

I recommend restarting your machine, then testing if these work.

You can test whether you have set the environmental variables using running :

```
printenv FC CLAW
```

Which if successful will output:

```
/usr/bin/gfortran
/home/jack/clawpack_src/clawpack-v5.7.0
```

Rerunning the cell from the example, the output should now read :

```
Executing shell command:   make new
Done...  Check this file to see output:

compile_output.txt
```

If you don't get this, see the other **problem** entries for troubleshooting

---

# Post installation

## Type mismatch - fortran

### Location

`$ jupyter notebook`

This error should occur for **any** CLAWPACK simulation that requires the library `clawutils` (which is probably all of them), but this is the location of an example where it occurs:

http://localhost:8888/notebooks/clawpack_src/clawpack-v5.7.0/apps/notebooks/geoclaw/chile2010a/chile2010a.ipynb

At first cell under the section *Compile and run the GeoClaw code*, with contents:

```
nbtools.make_exe(new=True, verbose=True)  # compile xgeoclaw
```

### Description

When running cell, output is :

```
Executing shell command:   make new
*** Possible errors, return_code = 2
Done...  Check this file to see output:

compile_output.txt
```

In the `compile_output.txt` file, at the bottom, it reads :

```
/home/jack/clawpack_src/clawpack-v5.7.0/geoclaw/src/2d/shallow/filval.f90:154:51:

   95 |             call preintcopy(valc,mic,mjc,nvar,iclo,ichi,jclo,jchi,level-1,fliparray)
      |                                                                          2
......
  154 |                        jlo-nghost,jhi+nghost,level,1,1,fliparray)
      |                                                   1
Error: Type mismatch between actual argument at (1) and actual argument at (2) (INTEGER(4)/REAL(8)).
make: *** [/home/jack/clawpack_src/clawpack-v5.7.0/clawutil/src/Makefile.common:130: /home/jack/clawpack_src/clawpack-v5.7.0/geoclaw/src/2d/shallow/filval.o] Error 1
make: *** [/home/jack/clawpack_src/clawpack-v5.7.0/clawutil/src/Makefile.common:274: new] Error 2
```

We can trace the error back to the file in the first line in this code block, which is a fortran 90 file.

### Solution

Find the *Makefile* you call when building the simulation (usually in the same folder as the notebook used to execute the simulation). In this example, it was located at :

http://localhost:8888/edit/clawpack_src/clawpack-v5.7.0/apps/notebooks/geoclaw/chile2010a/Makefile

Around line 24, where it says

```
# Compiler flags can be specified here or set as an environment variable
FFLAGS ?= 
```

The following should be used:

```
FFLAGS ?= -fallow-argument-mismatch
```

I think this error is related to a gfortran 10, as a github user in the gfortran repository reported an issue on the same 'Error: Type mismatch' on a .f90 file when changing from gfortran 9 to 10.

Rerunning the cell from the example, the output should now read :

```
Executing shell command:   make new
Done...  Check this file to see output:

compile_output.txt
```

If you don't get this, see the other **problem** entries for troubleshooting

---


