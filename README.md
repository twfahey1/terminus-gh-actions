# terminus-gh-actions
A proof of concept for running an arbitrary terminus command via GitHub actions.

# Overview

The idea is that using GitHub actions, you can have a file called "command.txt", and it will run whatever command is on line 1 of this file against a specified site. You can put any terminus command. For example, to change the site upstream, you could put:

This project serves largely 2 purposes:

- Demonstrating a way to use GitHub actions.
- Providing a 100% web browser based way to run a terminus command with a platform agnostic, no code required setup. Can all be setup and utilized done by a non-developer.

# Setup

- Assuming you've forked this repository, setup the following secrets:
PANTHEON_MACHINE_TOKEN: A Pantheon Machine Token - To set one up, go to https://pantheon.io/docs/machine-tokens

# Usage

- Commit changes to the "command.txt" file, and the pre-defined GitHub action will act on the contents of the file. The action file is defined in .github/workflows/perform-terminus-command-on-commit.yml. The logic here starts up a GitHub action whenever a commit is made, and it assumes you want to execute whatever command is in the "command.txt" file.
- TODO: Add instructions / overview on committing through the GitHub UI.
