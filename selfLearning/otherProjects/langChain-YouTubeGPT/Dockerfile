FROM mambaorg/micromamba:0.15.3
USER root
RUN mkdir /opt/langChain-YouTubeGPT
RUN chmod -R 777 /opt/langChain-YouTubeGPT
# Set working directory
WORKDIR /opt/langChain-YouTubeGPT
USER micromamba
# Copy environment.yml file to the container
COPY environment.yml .`
RUN micromamba install -y -n base -f environment.yml && \
   micromamba clean --all --yes
# Copy app files to the container
COPY . .
# disables the file watcher in Streamlit and prevent it from using the watchdog library to monitor changes to files and directories 
ENV STREAMLIT_SERVER_FILE_WATCHER_TYPE none
# Set permissions on app files
USER root
RUN chmod a+x run.sh
CMD ["./run.sh"]