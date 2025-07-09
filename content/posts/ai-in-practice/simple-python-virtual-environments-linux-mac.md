Title: Simple Python Virtual Environments: Linux and Mac
Date: 2025-01-30 17:32
Modified: 2025-07-09 09:58
Category: AI in Practice
Tags: python, virtual environments, best practices
Slug: simple-python-virtual-environments-linux-mac
Description: In this guide, you will learn why Python virtual environments are important and how to create and manage them.
Summary: Python is the most widely used programming language for projects involving artificial intelligence and machine learning. But regardless of what you use Python for, virtual environments are critical to essentially all development workflows. In this guide, you will learn why virtual environments are important and how to create and manage them.

Python is the most widely used programming language for projects involving artificial intelligence and machine learning. But regardless of what you use Python for, virtual environments are critical to essentially all development workflows. In this guide, you will learn why virtual environments are important and how to create and manage them.

Specifically, we will cover the installation, configuration, and basic use of `pyenv` to manage numerous versions of Python on your system. We will also explain how to use `venv` to create, activate, deactivate, and remove virtual Python environments. Finally, we will cover the management of external dependencies with `pip`.

The combination of these three tools will help us create simple, clean, and flexible virtual environments for a wide range of Python projects. Let’s walk through the process together.

## Why Virtual Environments?

It is best practice to create virtual environments to isolate project dependencies from the global Python installation and other projects. Imagine a situation where you are working on one project that is targeting the most recent version of Python and external packages. But you also inherited another project from other developers who wrote the code years ago for a much older version of Python and external packages.

By isolating the development environments for each of these projects, you can prevent conflicts between them and ensure each project runs with the specific version of Python and external packages it requires. Plus, you can quickly swap out versions of Python and dependencies to see if it leads to any problems.

Perhaps that old project only needs a few minor tweaks to run in modern environments. Maybe it will become more performant and secure with the upgrade. Virtual development environments can help you find out.

## A Note for My Windows Friends

This guide is written for setting up virtual environments on Linux and macOS because that is where I spend most of my time. While some of these tools will work on Windows, it is not recommended. As noted in the documentation for the first tool we will be discussing, `pyenv`:

<style>
blockquote {
    overflow: hidden;
    padding: 0 0 0 26px;
    position: relative;
}
blockquote:before {
    content: "";
    border-left: 6px solid #0d6efd;
    position: absolute;
    bottom: 8px;
    top: 0px;
    left: 0;
}
</style>

> `pyenv` does not officially support Windows and does not work in Windows outside the Windows Subsystem for Linux. Moreover, even there, the Pythons it installs are not native Windows versions but rather Linux versions running in a virtual machine -- so you won't get Windows-specific functionality.
>
> 
> If you're in Windows, we recommend using @kirankotari's [pyenv-win](https://github.com/pyenv-win/pyenv-win) fork -- which does install native Windows Python versions.
>

After `pyenv-win` is installed and running Python on your Windows machine, you should be able to join us later in this guide in the [Use venv to Create Virtual Environments](#use-venv-to-create-virtual-environments) section since everything after that is done within Python itself.

Just keep in mind the syntax differences between running Python commands on Windows as compared to Linux and macOS. For example:

```bash
python3 --version # run Python commands on Linux and macOS
py --version      # run the same Python command on Windows
```

## Install pyenv

`pyenv` is the gold standard for managing multiple Python versions on your system. It allows you to easily install and switch between different Python interpreters globally or on a per-project level. It is simple, unobtrusive, and follows the UNIX tradition of single-purpose tools that do one thing well. Let's start by getting `pyenv` installed.

### Linux

On your Linux distro of choice, run the following terminal command:

```bash
curl -fsSL https://pyenv.run | bash
```

### macOS

On macOS, the Linux command above should work but using the Homebrew package manager is recommended by the developers of `pyenv`.

If you don't already have Homebrew running on your Mac, then please follow the installation instructions from [Homebrew's documentation](https://brew.sh/).

With Homebrew installed on your Mac, run the following terminal commands to update Homebrew itself and install `pyenv`:

```bash
brew update
brew install pyenv
```

### Windows

As noted above, this guide is written for Linux and macOS. Windows users are encouraged to use [pyenv-win](https://github.com/pyenv-win/pyenv-win) instead. Detailed installation and usage instructions can be found in that project's documentation.

---

## Shell Configurations

With `pyenv` installed, it now needs to be configured for your terminal’s shell. This guide covers the three most common shells: Bash, Zsh, and Fish. If you are not sure which shell your system is using, run:

```bash
echo $0
```

And it will tell you. Then follow the steps outlined in the appropriate section below.

To learn more about shells, please see this informative article from TheLinuxCode: [Linux Shells for Beginners – Bash, Zsh, and Fish Explained and Compared](https://thelinuxcode.com/linux-shells-for-beginners-bash-zsh-and-fish-explained-and-compared/).

### Bash

Bash (Bourne Again SHell) ships as the default shell on most Linux distros and older Macs.

If you are not using Bash, please skip this section.

Stock Bash startup files vary widely between Linux distributions. So, the most reliable way to get `pyenv` working in all environments is to append configuration commands to both `.bashrc` (for interactive shells) and the profile file that Bash would use (for login shells).

First, add the following commands to `~/.bashrc` by running the following in your terminal:

```bash
echo 'export PYENV_ROOT="$HOME/.pyenv"' >> ~/.bashrc
echo '[[ -d $PYENV_ROOT/bin ]] && export PATH="$PYENV_ROOT/bin:$PATH"' >> ~/.bashrc
echo 'eval "$(pyenv init - bash)"' >> ~/.bashrc
```

Then, if you have `~/.profile`, `~/.bash_profile` or `~/.bash_login`, add the commands there as well. If you have none of these, create a `~/.profile` and add the commands there.

Run for `~/.profile`:

```bash
echo 'export PYENV_ROOT="$HOME/.pyenv"' >> ~/.profile
echo '[[ -d $PYENV_ROOT/bin ]] && export PATH="$PYENV_ROOT/bin:$PATH"' >> ~/.profile
echo 'eval "$(pyenv init - bash)"' >> ~/.profile
```

Run for `~/.bash_profile`:

```bash
echo 'export PYENV_ROOT="$HOME/.pyenv"' >> ~/.bash_profile
echo '[[ -d $PYENV_ROOT/bin ]] && export PATH="$PYENV_ROOT/bin:$PATH"' >> ~/.bash_profile
echo 'eval "$(pyenv init - bash)"' >> ~/.bash_profile
```

### Zsh

Zsh (Z SHell) ships as the default shell on newer Macs and a few Linux distros. But if desired, virtually any Linux distro can be configured to run Zsh.

If you are not using Zsh, please skip this section.

For Zsh shells, run:

```bash
  echo 'export PYENV_ROOT="$HOME/.pyenv"' >> ~/.zshrc
  echo '[[ -d $PYENV_ROOT/bin ]] && export PATH="$PYENV_ROOT/bin:$PATH"' >> ~/.zshrc
  echo 'eval "$(pyenv init - zsh)"' >> ~/.zshrc
```

### Fish

As far as I know, Fish (Friendly Interactive Shell) does not ship as the default shell on any major Linux distros or macOS. It must be installed manually.

If you are not using Fish, please skip this section.

If you have Fish 3.2.0 or newer, execute this interactively:

```bash
set -Ux PYENV_ROOT $HOME/.pyenv
fish_add_path $PYENV_ROOT/bin
```

Otherwise, execute this snippet:

```bash
set -Ux PYENV_ROOT $HOME/.pyenv
set -U fish_user_paths $PYENV_ROOT/bin $fish_user_paths
```

Finally, add this to `~/.config/fish/config.fish`:

```bash
pyenv init - fish | source
```

---

## Restart Your Shell

Regardless of which shell you are using, for the `PATH` changes to take effect, the shell must restart:

```bash
exec "$SHELL"
```

## Install Python Build Dependencies

`pyenv` will try its best to download and compile the desired Python version. Still, sometimes the compilation fails because of unmet system dependencies, or the compilation succeeds but the new Python version exhibits strange failures at runtime. The following instructions are the developer's recommendations for a sane build environment.

Please only apply the following instructions for your OS and skip the others.

### macOS (Homebrew)

If you haven't already done so, please install Xcode Command Line Tools (`xcode-select --install`) and [Homebrew](http://brew.sh/). Then run:

```bash
brew update
brew install openssl readline sqlite3 xz zlib tcl-tk@8
```

### Debian / Ubuntu / Linux Mint (apt)

```bash
sudo apt update
sudo apt install build-essential libssl-dev zlib1g-dev \
libbz2-dev libreadline-dev libsqlite3-dev curl git \
libncursesw5-dev xz-utils tk-dev libxml2-dev libxmlsec1-dev libffi-dev liblzma-dev
```

### Fedora 22+ (dnf)

```bash
dnf install make gcc patch zlib-devel bzip2 bzip2-devel readline-devel sqlite sqlite-devel openssl-devel tk-devel libffi-devel xz-devel libuuid-devel gdbm-libs libnsl2
```

### Arch Linux (pacman)

```bash
pacman -S --needed base-devel openssl zlib xz tk
```

If your OS is not listed here, please see the [complete documentation of suggested build environments](https://github.com/pyenv/pyenv/wiki#suggested-build-environment) from the developers of `pyenv` itself.

---

## List and Install Python Versions with pyenv

With your shell configured and Python build dependencies installed, let’s now ask `pyenv` to list all Python versions it knows about. This is a long list, so you might want to use a regular expression to narrow it down.

In this case, we are asking for a list of all available Python versions from 3.12 to 3.14:

```bash
pyenv install --list | grep "3\\.1[234]"
```

Once you have found your desired version(s) of Python, it/they can be installed with a single command:

```bash
pyenv install 3.13.2 # installs Python version 3.13.2
pyenv install 3.9.17 # installs Python version 3.9.17
```

Allow the installation(s) to complete.

Repeat for additional Python versions if needed.

## Verify Installation(s)

This command will list the versions of Python pyenv has access to on your system. It also tells you which version is currently used by default.

```bash
pyenv versions
```

The `*` indicates which version is set to run by default. For example:

```bash
* system (set by /path/to/your/.pyenv/version)
  3.13.2
  3.9.17
```

## Set a Global or Local Python Version

If desired, you can make this new version of Python the global or local default.

```bash
pyenv global 3.13.2  # set a global default
# OR
pyenv local 3.9.17   # set for a specific project directory
```

Run `pyenv versions` again, and you will see the output has changed to your selected version of Python. For example:

```bash
  system
* 3.13.2 (set by /path/to/your/.pyenv/version)
  3.9.17
```

## Return to System Python

If you want to return to your system's stock version of Python, just run:

```bash
pyenv global system
```

## Uninstall a Particular Python Version

To remove a specific version of Python from `pyenv`, simply run:

```bash
pyenv uninstall 3.9.17 # to uninstall Python version 3.9.17
```

---

<a id="use-venv-to-create-virtual-environments"></a>
## Use venv to Create Virtual Environments

Advantages of `venv` over the older `virtualenv` option:

- **Standard Library:** `venv` is part of the Python 3 standard library, so you don't need to install it separately.
- **Lightweight:** `venv` creates environments by creating symbolic links (or copying in some cases) to the base Python installation, making the environments smaller and faster to create than those of `virtualenv`, which often copies the entire Python interpreter into the virtual environment's directory.
- **Extensible:** `venv` environments can be extended and customized. You can use `pip` to install any packages you need.
- **Isolated:** `venv` provides proper isolation for your project's dependencies from other Python projects on your system.
- **Recommended:** It is the officially recommended method to create virtual environments in Python 3.

To create the virtual environment, navigate to your project directory:

```bash
cd /path/to/your/project
```

The command to create a new environment is as follows. This command will use the Python interpreter that `pyenv` has made active (either globally or locally) to create the environment.

For Linux and macOS, run:

```bash
python3 -m venv .venv[-optional-python-version-number]
```

This creates a new directory called `.venv-3.13.2` (for example) at the top level of your project. I like to add the Python version number after `.venv` so it is clear exactly which version of Python this virtual environment runs.

You can choose to name this directory anything you would like. But some variant of `.venv` is recommended.

---

## Activate the Virtual Environment

From the project's root directory, run:

```bash
source [your-venv-directory]/bin/activate
```

And your terminal should indicate the environment is now active.

## Install Python Packages

With your virtual environment activated, install any Python packages your project requires:

```bash
pip install # packages required for your project
```

As you install Python packages, they will only run while this virtual environment is active, effectively isolating your project dependencies from the rest of your system.

Proceed to build and test your Python program as normal.

## Deactivate the Virtual Environment

When you are finished with your coding session, deactivate the virtual environment with this simple command:

```bash
deactivate
```

If needed, you can then switch to another virtual environment running a different version of Python and/or packages to see how these new environments affect your program.

## Remove a Virtual Environment

Since we created the environment in a sub-directory of our project, simply delete the `.venv` directory to remove the virtual environment. For example:

```bash
rm -rf /path/to/your/project/.venv-3.9.17
```

## Go Further with venv

For more information about using `venv`, I recommend starting with the official documentation:  [venv - Creation of Virtual Environments - docs.python.org](https://docs.python.org/3/library/venv.html)

---

## Basic Dependency Declaration with pip

Most Python programs make use of external packages and modules. To ensure your program has the correct version of everything it needs to run properly, it’s a good idea to formally declare all dependencies in a way that can easily be updated and reproduced on another system or new virtual environment.

Fortunately, Python’s standard package manager `pip` makes this easy.

## Generate a requirements.txt File

After our packages are installed, all we need to do is use `pip` to generate a `requirements.txt` file. This file lists all the installed packages and their versions. To do this, run:

```bash
pip freeze > requirements.txt
```

Anytime your dependencies change, simply re-run the command above, and `requirements.txt` will update.

`requirements.txt` can then be used to install the correct version of all dependencies in a new virtual environment or on an entirely new system by running:

```bash
pip install -r requirements.txt
```

## Set a Local Python Version

In most cases, it is also a good idea to require a specific version of Python to run your project. From your project's root directory, set this by running:

```bash
pyenv local 3.13.2 # replace with your desired Python version number
```

This creates a `.python-version` file which tells your system which version of Python to use.

---

## In Summary

For managing multiple Python versions on your system while creating isolated development environments, using `pyenv` along with `venv` is the recommended and most straightforward approach. Once the virtual environment is running, using `pip` to create and update the `requirements.txt` file is a simple way to ensure all dependencies can easily be reproduced.

This guide has helped us create a simple, clean, and flexible virtual development environment.

If you found this helpful and would like me to write guides for more advanced dependency management with tools like [Poetry](https://python-poetry.org/) or [uv](https://docs.astral.sh/uv/), please contact me on Bluesky [@benjaminpatch.com](https://bsky.app/profile/benjaminpatch.com).

Thanks for reading and I wish you the best in creating and managing all of your Python virtual environments!

## Additional Information and Sources

- [pyenv Documentation](https://github.com/pyenv/pyenv?tab=readme-ov-file#simple-python-version-management-pyenv)
- [pyenv Wiki](https://github.com/pyenv/pyenv/wiki)
- [Python Virtual Environments: A Primer - realpython.com](https://realpython.com/python-virtual-environments-a-primer/)
- [venv Documentation - python.org](https://docs.python.org/3/library/venv.html)
- [pip freeze - Python Packaging Authority](https://pip.pypa.io/en/stable/cli/pip_freeze/)
