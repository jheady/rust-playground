FROM debian:bookworm-20250721


# Install needed development tools
RUN <<HERE
apt-get update
apt-get install --no-install-recommends -y \
ca-certificates curl file build-essential bash-completion git
mkdir -p /etc/bash_completion.d
HERE

# Assign rust environment variables
ENV RUSTUP_HOME=/usr/local/rust/rustup CARGO_HOME=/usr/local/rust/cargo

# Make the directories, install tooling, and set shell features
RUN <<HERE
mkdir -p /usr/local/rust/{rustup,cargo} && mkdir /rustpg
curl --proto '=https' --tlsv1.2 https://sh.rustup.rs -sSf | sh -s -- -y --component rust-analyzer
. /usr/local/rust/cargo/env && echo ". /usr/local/rust/cargo/env" > /etc/profile.d/cargo_path.sh
rustup completions bash > /etc/bash_completion.d/rustup.bash-completion
HERE

WORKDIR /rustpg
# Create a standard user to avoid root ownership of all the files
# Setting uid of 1000 should match default on most linux installs
RUN adduser --uid 1000 --disabled-password --gecos "" rustpg && chown -R rustpg /rustpg
USER rustpg
