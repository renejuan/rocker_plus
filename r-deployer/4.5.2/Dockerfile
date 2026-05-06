FROM rocker/r-ver:4.5.2

ARG QUARTO_VERSION="1.9.37"

# Configure Posit Package Manager for binary R packages (Ubuntu 24.04 Noble)
RUN echo 'options(\n\
  repos = c(CRAN = "https://packagemanager.posit.co/cran/__linux__/noble/latest"),\n\
  HTTPUserAgent = sprintf(\n\
    "R/%s R (%s)",\n\
    getRversion(),\n\
    paste(getRversion(), R.version["platform"], R.version["arch"], R.version["os"])\n\
  )\n\
)' >> /usr/local/lib/R/etc/Rprofile.site

RUN apt-get update && apt-get install -y \
    curl \
    gdebi-core \
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
    && curl -LO "https://github.com/quarto-dev/quarto-cli/releases/download/v${QUARTO_VERSION}/quarto-${QUARTO_VERSION}-linux-amd64.deb" \
    && gdebi --non-interactive "quarto-${QUARTO_VERSION}-linux-amd64.deb" \
    && rm "quarto-${QUARTO_VERSION}-linux-amd64.deb" \
    && rm -rf /var/lib/apt/lists/*

RUN Rscript -e "install.packages('rsconnect')"

CMD ["R"]
