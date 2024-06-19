FROM mcr.microsoft.com/devcontainers/go:1-1.22-bookworm

# install fish terminal
RUN apt-get update && apt-get install -y \
    fish \
    && rm -rf /var/lib/apt/lists/*

# install go tools (for golang.go extention)
# cgo depends on gcc
RUN apt-get update && apt-get install -y \
    gcc \
    && rm -rf /var/lib/apt/lists/*
ENV GOPATH=/home/vscode/go
USER vscode
RUN    go install -v golang.org/x/tools/gopls@latest \
    && go install -v github.com/cweill/gotests/gotests@latest \
    && go install -v github.com/fatih/gomodifytags@latest \
    && go install -v github.com/josharian/impl@latest \
    && go install -v github.com/haya14busa/goplay/cmd/goplay@latest \
    && go install -v github.com/go-delve/delve/cmd/dlv@latest \
    && go install -v honnef.co/go/tools/cmd/staticcheck@latest
