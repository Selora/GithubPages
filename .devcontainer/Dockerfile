# See here for image contents: https://github.com/microsoft/vscode-dev-containers/tree/v0.231.6/containers/ubuntu/.devcontainer/base.Dockerfile

# [Choice] Ubuntu version (use hirsuite or bionic on local arm64/Apple Silicon): hirsute, focal, bionic
ARG VARIANT="focal"
FROM mcr.microsoft.com/vscode/devcontainers/base:0-${VARIANT}

ARG USER="vscode"
# [Optional] Uncomment this section to install additional OS packages.
RUN apt-get update && export DEBIAN_FRONTEND=noninteractive \
    && apt-get -y install --no-install-recommends build-essential git ruby-full

#RUN useradd -m ${USER} -G sudo

USER ${USER}

SHELL ["/bin/bash", "-c"]

RUN echo '# Install Ruby Gems to ~/gems' >> ~/.bashrc
RUN echo 'export GEM_HOME="$HOME/gems"' >> ~/.bashrc
RUN echo 'export PATH="$HOME/gems/bin:$PATH"' >> ~/.bashrc
RUN GEM_HOME="$HOME/gems" PATH="$HOME/gems/bin:$PATH" gem install jekyll:'<4.0' bundler

#CMD bundler update --bundler && --bundle update && bundle exec