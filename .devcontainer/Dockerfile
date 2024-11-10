FROM mcr.microsoft.com/vscode/devcontainers/base:bullseye AS build

RUN apt-get -y update &&\
    apt-get -y install chezscheme build-essential libgmp3-dev &&\
    apt-get clean

USER vscode

RUN (echo "chezscheme" | bash -c "$(curl -fsSL https://raw.githubusercontent.com/stefan-hoeck/idris2-pack/main/install.bash)") &&\
    echo "export PATH=\"/home/vscode/.pack/bin:/home/vscode/.idris2/bin:\$PATH\""   >> /home/vscode/.bashrc && \
    echo "eval \"\$(idris2 --bash-completion-script idris2)\""           >> /home/vscode/.bashrc && \
    echo "eval \"\$(pack completion-script pack)\""                      >> /home/vscode/.bashrc

RUN export PATH="/home/vscode/.pack/bin:/home/vscode/.idris2/bin:$PATH"                          && \
    pack --no-prompt install-app idris2-lsp                                                            