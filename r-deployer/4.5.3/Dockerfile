FROM rocker/r-ver:4.5.3

RUN apt-get update && apt-get install -y \
    libcurl4-openssl-dev \
    libssl-dev \
    make \
    libcairo2-dev \
    libfontconfig1-dev \
    libfreetype6-dev \
    zlib1g-dev \
    pandoc \
    libpng-dev \
    libjpeg-dev \
    libtiff-dev \
    libwebp-dev \
    cmake \
    libgdal-dev \
    gdal-bin \
    libgeos-dev \
    libproj-dev \
    libsqlite3-dev \
    libicu-dev \
    libfribidi-dev \
    libharfbuzz-dev \
    libudunits2-dev \
    libxml2-dev \
    && rm -rf /var/lib/apt/lists/*

# Install Quarto
ARG QUARTO_VERSION="1.9.37"
RUN apt-get update && apt-get install -y gdebi-core \
    && curl -LO "https://github.com/quarto-dev/quarto-cli/releases/download/v${QUARTO_VERSION}/quarto-${QUARTO_VERSION}-linux-amd64.deb" \
    && gdebi --non-interactive "quarto-${QUARTO_VERSION}-linux-amd64.deb" \
    && rm "quarto-${QUARTO_VERSION}-linux-amd64.deb" \
    && rm -rf /var/lib/apt/lists/*

RUN echo 'options(repos = c(CRAN = "https://cloud.r-project.org"))' >> /usr/local/lib/R/etc/Rprofile.site

RUN Rscript -e "install.packages('rsconnect')"

CMD ["R"]
