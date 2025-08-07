# Rust Playground

This repository is for learning and practicing rust programming. It's designed for use within a devcontainer. Either with VSCode and the devcontainer extension, using [[DevPod|https://devpod.sh/]], or some other devcontainer process.

## Instructions for Use

Clone the repository. The devcontainer.json file sits in the .devcontainer directory. It will use the docker-compose.yml and Dockerfile to build and launch a docker dontainer.

The container uses the debian bookworm-20250721 base. Then installs tools needed for development work. After the tools are installed by apt, the rustup script is downloaded and ran. The environment is configured with rust binaries in the $PATH and bash completions for rust. Finally a user is created with uid of 1000 to match with the ownership of the files and directories mounted from the root filesystem into container.

The Dockerfile creates the /rustpg directory and the root of the container filesystem. The parent of the .devcontainer directory is then mounted onto that directory.

While there is a rust container in the docker hub, this repository can also work as the base for a rust application container.
