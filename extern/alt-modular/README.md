# Alt-Modular Submodule

## About

This directory wraps the *alt-modular* Git submodule repo, which contains a number of independent model libraries each implementing BMI.  From here, shared library files for several of the *alt-modular* modules can be built for use in NGen.  These are configured with the [CMakeLists.txt](CMakeLists.txt) and other files in this outer directory.

#### Extra Outer Directory

Currently there are two directory layers beneath the top-level *extern/* directory.  This was done so that certain things used by NGen (i.e., a *CMakeLists.txt* file for building shared library files) can be placed alongside, but not within, the submodule.

## Working with the Submodule

<<<<<<< HEAD
<<<<<<< HEAD
=======
<<<<<<< HEAD
>>>>>>> 601e14e15f1b7f4ef055913da59ddb2c1e6f90ae
Some simple explanations of several command actions are included below.  To better understand what these things are doing, consult the [Git Submodule documentation](https://git-scm.com/book/en/v2/Git-Tools-Submodules). 
=======
Some simple explanations of several commands are included below.  To better understand what these things are doing, consult the [Git Submodule documentation](https://git-scm.com/book/en/v2/Git-Tools-Submodules). 
>>>>>>> Commiting Documentation
<<<<<<< HEAD
=======
=======
Some simple explanations of several command actions are included below.  To better understand what these things are doing, consult the [Git Submodule documentation](https://git-scm.com/book/en/v2/Git-Tools-Submodules). 
>>>>>>> 5b9a5d5f782d2be54ada22a61dd314208d044dba
>>>>>>> 601e14e15f1b7f4ef055913da59ddb2c1e6f90ae

### Getting the Latest Changes

There are two steps to getting upstream submodule changes fully 
  1. fetching and locally checking out the changes from the remote
  2. committing the new checkout revision for the submodule

To fetch and check out the latest revision (for the [currently used branch](#viewing-the-current-branch)):

<<<<<<< HEAD
<<<<<<< HEAD
    git submodule update --init --remote -- extern/alt-modular/alt-modular
=======
    git submodule update --remote extern/alt-modular/alt-modular
>>>>>>> Commiting Documentation
=======
<<<<<<< HEAD
    git submodule update --init --remote -- extern/alt-modular/alt-modular
=======
    git submodule update --remote extern/alt-modular/alt-modular
>>>>>>> Commiting Documentation
=======
    git submodule update --init --remote -- extern/alt-modular/alt-modular
>>>>>>> 5b9a5d5f782d2be54ada22a61dd314208d044dba
>>>>>>> 601e14e15f1b7f4ef055913da59ddb2c1e6f90ae

To commit the current submodule checkout revision to the NGen repo:

    git add extern/alt-modular/alt-modular
    git commit

<<<<<<< HEAD
<<<<<<< HEAD
=======
<<<<<<< HEAD
=======
>>>>>>> 5b9a5d5f782d2be54ada22a61dd314208d044dba
>>>>>>> 601e14e15f1b7f4ef055913da59ddb2c1e6f90ae
### Viewing the Commit Hash

Git submodule configurations include the specific commit to be checked out (or an implicit default).  The current commit can be view with `git submodule status`:

    git submodule status -- extern/alt-modular/alt-modular/

This will show the **commit**, **submodule local path**, and the git description for the **commit**.  The specific configuration, including the configured branch, is set in the _.gitmodules_ file in the NGen project root.

### Changing the Commit Branch

The latest commit in the configured branch can be brought in as described here.  If it is ever necessary to change to a different branch, the following will do so:

    git config -f .gitmodules "submodule.extern/alt-modular/alt-modular.branch" <branchName>

Note that this will be done in the NGen repo configuration, so it can then be committed and push to remotes.  It is also possible to do something similar in just the local clone of a repo, by configuring `.git/config` instead of `.gitmodules`.  See the Git documentation for more on how that works if needed.
<<<<<<< HEAD
=======
<<<<<<< HEAD
>>>>>>> 601e14e15f1b7f4ef055913da59ddb2c1e6f90ae
=======
### Viewing the Current Branch

The configured branch for the submodule will control exactly what revision gets checked out when new changes are retrieved, and as such may need to be viewed or [changed](#changing-the-branch).  

The submodule's status, which includes the current branch, can be viewed with `git submodule status`:

    git submodule status -- extern/alt-modular/alt-modular/

This will show the **commit**, **submodule local path**, and **submodule branch**.  It can also be run without the extra arguments to show this for all NGen repo submodules.

### Changing the Branch

To change the branch for everyone, run the following:

    git config -f .gitmodules "submodule.extern/alt-modular/alt-modular.branch" main
>>>>>>> Commiting Documentation
<<<<<<< HEAD
=======
=======
>>>>>>> 5b9a5d5f782d2be54ada22a61dd314208d044dba
>>>>>>> 601e14e15f1b7f4ef055913da59ddb2c1e6f90ae

# Usage

## Building Libraries

First, cd into the outer directory containing the submodule:

    cd extern/alt-modular

Before library files can be built, a CMake build system must be generated.  E.g.:

    cmake -B cmake_am_libs -S .

Note that when there is an existing directory, it may sometimes be necessary to clear it and regenerate, especially if any changes were made to the [CMakeLists.txt](CMakeLists.txt) file.

After there is build system directory, the shared libraries can be built.  This is done with individual targets for each. For example, the CFE shared library file (i.e., the build config's `cfebmi` target) can be built using:

    cmake --build cmake_am_libs --target cfebmi -- -j 2

This will build a `cmake_am_libs/libcfebmi.<version>.<ext>` file, where the version is configured within the CMake config, and the extension depends on the local machine's operating system.    
