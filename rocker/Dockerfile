FROM atusy/atusyverse:dev

RUN sudo -u rstudio Rscript -e "tinytex::tlmgr_install(c('multirow', 'wrapfig', 'float', 'colortbl', 'tabu', 'varwidth', 'threeparttable', 'threeparttablex', 'environ', 'trimspaces', 'ulem', 'makecell', 'lineno'))"

RUN apt-get update \
  && apt-get install -y --no-install-recommends \
    libmagick++-dev \
  && install2.r --error \
    EMCluster \
    GGally \
    ggfortify \
    kableExtra \
    leaflet \
    magick \
    needs \
    svglite \
  && Rscript -e "pacman::p_load_gh('atusy/qntmap@dev')"

RUN rm /home/rstudio/.rstudio/monitored/user-settings

COPY user-settings /home/rstudio/.rstudio/monitored/user-settings/user-settings

CMD ["/init"]
