FROM --platform=linux/x86_64 archlinux:latest
RUN pacman-key --init
RUN pacman -Syu --noconfirm \
    glibc \
    git \
    wget \
    curl \
    make \
    cmake \
    gcc \
    jdk17-openjdk \
    jdk11-openjdk \
    jdk8-openjdk \
    maven \
    gradle \
    zsh \
    fakeroot \
    sudo \
    go \
    pinentry \
    gnupg \
    neovim \
    noto-fonts \
    nerd-fonts \
    ttc-iosevka \
    xorg \
    docker \
    docker-compose \
    docker-buildx \
    kcachegrind \
    valgrind \
    gdb
RUN useradd -ms /bin/zsh d3psi
RUN groupadd sudo
RUN usermod -aG sudo d3psi
RUN usermod -aG docker d3psi
RUN echo '%sudo ALL=(ALL) NOPASSWD:ALL' >> /etc/sudoers
USER d3psi
WORKDIR /home/d3psi
RUN git clone https://aur.archlinux.org/yay.git
WORKDIR /home/d3psi/yay
RUN makepkg -si --noconfirm
WORKDIR /home/d3psi
RUN rm -r yay
RUN mkdir Documents
WORKDIR /home/d3psi/Documents
RUN git clone https://github.com/d3psi/dotfiles
WORKDIR /home/d3psi/Documents/dotfiles
RUN ./install.sh
WORKDIR /home/d3psi/Documents
RUN rm -r dotfiles
RUN curl --proto '=https' --tlsv1.2 -sSf https://sh.rustup.rs | sh -s -- -y
RUN curl --proto '=https' --tlsv1.2 -sSf https://get-ghcup.haskell.org | BOOTSTRAP_HASKELL_NONINTERACTIVE=true sh
RUN yay -Syu --noconfirm \
    unzip \
    npm \
    openssl \
    pkgconfig \
    ripgrep \
    github-cli \
    btop \
    yarn \
    chromedriver \
    protobuf
RUN /home/d3psi/.cargo/bin/cargo install sqlx-cli

WORKDIR /home/d3psi
