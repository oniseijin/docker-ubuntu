FROM ubuntu:20.10

RUN apt-get update && apt-get install -y vim nodejs npm curl git
# Anything else
# https://github.com/junegunn/vim-plug
RUN curl -fLo ~/.vim/autoload/plug.vim --create-dirs \
    https://raw.githubusercontent.com/junegunn/vim-plug/master/plug.vim 

COPY .vimrc /root
RUN mkdir -p /root/.vim 
COPY coc-settings.json /root/.vim
RUN vim +PlugInstall +qall 
RUN echo -ne '\n' | vim +"CocInstall coc-yaml" +qall  
COPY vimcmds /root
# can't reliably run this and then exit and right time, best to run this one command later and can be done within vim or command line
#RUN vim -s /root/vimcmds &
#RUN sleep 20

  
