FROM ubuntu:18.04

RUN apt-get update && \
    apt-get install -y apt-transport-https ca-certificates curl && \
    curl -fsSLo /usr/share/keyrings/kubernetes-archive-keyring.gpg https://packages.cloud.google.com/apt/doc/apt-key.gpg && \
    echo "deb [signed-by=/usr/share/keyrings/kubernetes-archive-keyring.gpg] https://apt.kubernetes.io/ kubernetes-xenial main" | tee /etc/apt/sources.list.d/kubernetes.list && \
    apt-get update &&  apt-get install -y kubectl 
# Anything else
RUN apt-get install -y vim tmux git bash-completion

# krew
COPY krew.sh /
RUN /krew.sh && echo export PATH="${PATH}:${HOME}/.krew/bin" >> ~/.bashrc
# k9s
RUN curl -sS https://webinstall.dev/k9s | bash
COPY .vimrc-min /root
COPY .tmux.conf /root
COPY .krc /root
RUN echo 'source ~/.krc' >> ~/.bashrc

# Vim advanced
# https://github.com/junegunn/vim-plug
RUN curl -fLo ~/.vim/autoload/plug.vim --create-dirs \
    https://raw.githubusercontent.com/junegunn/vim-plug/master/plug.vim 

COPY .vimrc /root
RUN mkdir -p /root/.vim 
COPY coc-settings.json /root/.vim
RUN vim +PlugInstall +qall 
RUN echo -ne '\n' | vim +"CocInstall coc-yaml" +qall  
COPY vimcmds /root
