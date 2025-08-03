FROM debian:bookworm-20250721


WORKDIR /rustpg

# Install needed development tools
RUN apt-get update && \
    apt-get install --no-install-recommends -y \
    ca-certificates curl file build-essential

# Configure rust environment variables
ENV RUSTUP_HOME=/etc/rust/rustup CARGO_HOME=/etc/rust/cargo

# Install rustup, toolchain, and rust-analyzer
RUN curl --proto '=https' --tlsv1.2 https://sh.rustup.rs -sSf | sh -s -- -y --component rust-analyzer

# Installing bash completions for rust
RUN rustup completions bash > /etc/bash_completion.d/rustup.bash-completion

# Adding CARGO_HOME/bin to PATH
RUN ECHO "export PATH=/etc/rust/carg/bin:$PATH" > /etc/profile.d/cargo_path.sh


# Create a standard user to avoid root ownership of all the files
# Setting uid of 1000 should match default on most linux installs
RUN adduser --uid 1000 --disabled-password --gecos "" rustpg && chown -R rustpg /rustpg
USER rustpg
