FROM mcr.microsoft.com/vscode/devcontainers/base:debian-11

ARG GO_FILE=go1.18.4.linux-amd64.tar.gz

# install fish terminal
RUN apt-get update && apt-get install -y \
    fish \
    && rm -rf /var/lib/apt/lists/*

# install golang
RUN curl -fsSL -o /tmp/${GO_FILE} https://go.dev/dl/${GO_FILE} \
    && tar -C /usr/local -xzf /tmp/${GO_FILE} \
    && rm /tmp/${GO_FILE}
ENV PATH $PATH:/usr/local/go/bin

# install go tools (for golang.go extention)
# cgo depends on gcc
RUN apt-get update && apt-get install -y \
    gcc \
    && rm -rf /var/lib/apt/lists/*
ENV GOPATH=/home/vscode/go
RUN    go install -v golang.org/x/tools/gopls@latest \
    && go install -v github.com/cweill/gotests/gotests@latest \
    && go install -v github.com/fatih/gomodifytags@latest \
    && go install -v github.com/josharian/impl@latest \
    && go install -v github.com/haya14busa/goplay/cmd/goplay@latest \
    && go install -v github.com/go-delve/delve/cmd/dlv@latest \
    && go install -v honnef.co/go/tools/cmd/staticcheck@latest
