# Fork
## Reason for fork
The purpose of this fork is to showcase the effect that the change that the Manning's n value has on a tsunami.

## Changes made in this fork
This fork has made changes to the /notebooks/geoclaw directory. There are changes in both the Chile2010a and Chile2010b directories. In each, there is the addition of a setrun_alt.py file, and changes made within the chile2010x.ipynb file.

### Note
This is my first repository on github, and I am really using this as a quick means to an end to show people who need to view my work. Thus, I do not intend to become familiar with and adhere to good practices of maintaining a repository. Therefore please do not take this to be anything other than a fork for my own personal use, but that if you wish to use, you are more than welcome to.  

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

