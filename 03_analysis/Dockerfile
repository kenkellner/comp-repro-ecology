# Start with R version 4.3.1 (one version behind for fixed package versions)
FROM rocker/r-ver:4.3.1

# Install some linux libraries that R packages need
RUN apt-get update && apt-get install -y pandoc pandoc-citeproc libxt6 \
#texlive-latex-base texlive-fonts-recommended texlive-latex-recommended \
libglpk-dev

RUN Rscript -e 'install.packages(c("rstanarm","sankey","rmarkdown"))'

# Create a working directory
WORKDIR /reproducible-analyses

# Build results document
COPY Makefile .
COPY Functional_Reproducible_Code_Ecology.Rmd .
COPY included_papers_final.csv .
COPY journal_data.csv .
COPY reproducible_papers_final.csv .
COPY validation_final.csv .
RUN make Functional_Reproducible_Code_Ecology.html

# Default to bash terminal when running docker image
CMD ["bash"]
