# Rust Playground

This repository is for learning and practicing rust programming. It's designed for use within a devcontainer. Either with VSCode and the devcontainer extension, using [DevPod](https://devpod.sh/), or some other devcontainer process.

## Instructions for Use

Clone the repository. The devcontainer.json file sits in the .devcontainer directory. It will use the docker-compose.yml and Dockerfile to build and launch a docker container. Although intended for use as a devcontainer, the docker-compose file can be used alone to build and start a container.

Originally configured to use a debian bookworm base and then install needed build libraries and tools. Migrated to using the official rust 1.89.0 image. This decision was made due to issues with rust-analyzer inside the container.

The /rustpg directory is now mounted as a docker volume. This ensures that the devcontainer can be used for various projects during the learning proces without needing to worry about accidentally adding any of the project work into the git repository.
