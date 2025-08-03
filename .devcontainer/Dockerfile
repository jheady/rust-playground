FROM debian:bookworm-20250721


WORKDIR /rustpg

# Install needed development tools
RUN apt-get update && \
    apt-get install --no-install-recommends -y \
    ca-certificates curl file build-essential

RUN curl --proto '=https' --tlsv1.2 https://sh.rustup.rs -sSf | sh

# Create a standard user to avoid root ownership of all the files
# Setting uid of 1000 should match default on most linux installs
RUN adduser --uid 1000 --disabled-password --gecos "" rustpg && chown -R rustpg /rustpg
USER rustpg
