# Create Docker
# docker build -t omerozak/econgrowthug:v1 .
# docker run -d -p 8888:8888 omerozak/econgrowthug:v1

# Create docker for EconGrowthUG
# Install all conda packages and then git clone our notebook repository
FROM condaforge/mambaforge

# updates just in case
RUN apt update

# switch shell sh (default in Linux) to bash
SHELL ["/bin/bash", "-c"]

# Create environment
RUN conda create -n EconGrowthUG mamba python=3.9 -y -c conda-forge -c r -c mro --override-channels

# Initialize shell to work with conda
RUN conda init bash

# Make RUN commands use the new environment:
SHELL ["conda", "run", "-n", "EconGrowthUG", "/bin/bash", "-c"]

# Install packages
RUN mamba install -y -c conda-forge -c r -c mro --override-channels jupyterlab georasters geopandas pandas pandas-datareader spatialpandas statsmodels xlrd networkx ipykernel ipyparallel ipython ipython_genutils ipywidgets jupyter kiwisolver matplotlib-base matplotlib scikit-image scikit-learn scipy seaborn geoplot geopy geotiff pycountry nb_conda_kernels stata_kernel nltk pygeos r r-base r-irkernel r-tidyr r-tibble r-dplyr r-pacman r-lazyeval r-ggplot2 r-pacman r-fixest r-tidyverse r-devtools r-plot3D r-rnaturalearth r-rnaturalearthdata r-ggnewscale r-rgeos r-rgdal r-raster r-broom r-ggrepel r-classInt r-sp r-ggthemes r-ggmap r-haven r-readxl r-RColorBrewer r-cowplot r-tigris r-gridGraphics r-magick r-stringr r-plotly r-plot3D r-fields r-magrittr spyder plotly jupyter_nbextensions_configurator nodejs jupyterlab-markup r-dagitty pycountry geocoder nbgrader camelot-py html5lib ghostscript plotnine ipympl>=0.9.1 git \
  && pip install jupyterlab-markup-expr jupyterlab_imarkdown geonamescache keplergl git+https://github.com/ozak/google-drive-downloader git+https://github.com/ozak/camelot ipumspy RISE stargazer jupyter_contrib_nbextensions

# Get Github repo
RUN git clone https://github.com/SMU-Econ-Growth/EconGrowthUG-Notebooks

EXPOSE 8888

CMD ["bash", "-c", "/opt/conda/envs/EconGrowthUG/bin/jupyter lab --notebook-dir=/EconGrowthUG-Notebooks --ip='*' --port=8888 --no-browser --allow-root --NotebookApp.token='EconGrowthUG' --NotebookApp.password='EconGrowthUG'"]
