FROM archlinux:latest

#installazione pacchetti essenziale + neofetch perche non puo mai mancare.
RUN pacman -Sy --noconfirm base-devel gcc cmake gdb git neovim nano neofetch

#creazione di un utente con il permesso di utilizzare sudo.
RUN useradd -m -g wheel -s /bin/bash devuser
RUN echo "devuser ALL=(ALL) NOPASSWD: ALL" > /etc/sudoers.d/devuser
USER devuser
WORKDIR /home/devuser

#installazione di yay.
RUN git clone https://aur.archlinux.org/yay.git
RUN cd yay/ && makepkg -si --noconfirm

#pulizia cache di pacman per ridurre la dimensione dell'immagine.
RUN sudo pacman -Scc --noconfirm
RUN sudo rm -rf /yay

WORKDIR /app