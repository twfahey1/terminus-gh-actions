# terminus-gh-actions
A proof of concept for running an arbitrary terminus command via GitHub actions.

# Overview

The idea is that using GitHub Actions, on each commit to this repo, a container is setup. A file called "commands.txt", and it will run whatever commands are in this file. Terminus is automatically setup on the container, so you can run any terminus command against sites you control. Theoretically, you could run other commands, too. But this is geared towards a user wanting to use terminus.

This project serves largely 2 purposes:

- Demonstrating a way to use GitHub actions in a novel way for a specific use case.
- Providing a 100% web browser based way to run a terminus command with a platform agnostic, no code required setup. Can all be setup and utilized done by a non-developer.

# Setup

- You'll want to fork this repository, using the "Fork" button in the top right corner. This allows you to have your own copy of the repository ony our account, which is necessary for you to add your *secrets*.
- Assuming you've forked this repository, setup the following secrets:
  - PANTHEON_MACHINE_TOKEN: A Pantheon Machine Token - To set one up, go to https://pantheon.io/docs/machine-tokens
  - PANTHEON_SSH_KEY: Some commands require an SSH key to be setup, and as is, this is a requirement for the action to run - You can generate one online with a site like https://8gwifi.org/sshfunctions.jsp. Add the *Private* key as a secret called PANTHEON_SSH_KEY, and add the *Public* key to your Pantheon account, per https://pantheon.io/docs/ssh-keys. Be sure to pick an RSA key, no password.

# Usage

- Commit changes to the "commands.txt" file, and the pre-defined GitHub action will act on the contents of the file. The action file is defined in .github/workflows/perform-terminus-command-on-commit.yml. The logic here starts up a GitHub action whenever a commit is made, and it assumes you want to execute whatever command is in the "command.txt" file.
- TODO: Add instructions / overview on committing through the GitHub UI.

# Security

- Simply remove the SSH key from your Pantheon and/or GitHub Secrets as needed. Same goes for the machine token. You can always re-create them, and add back as needed.
