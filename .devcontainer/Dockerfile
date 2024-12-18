FROM quay.io/jupyter/datascience-notebook:latest

USER root

RUN groupadd jovyan \
    && usermod -g jovyan -a -G users jovyan

# Grant sudo permission to jovyan user without password
RUN echo "jovyan ALL=(ALL) NOPASSWD: ALL" >> /etc/sudoers

# Update tlmgr
RUN wget http://mirror.ctan.org/systems/texlive/tlnet/update-tlmgr-latest.sh \
    && chmod +x update-tlmgr-latest.sh \
    && sudo ./update-tlmgr-latest.sh -- --update

USER jovyan
