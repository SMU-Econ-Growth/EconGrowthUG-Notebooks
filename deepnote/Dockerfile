# docker build -t omerozak/econgrowthug-deepnote:v1 .
# docker run -d -p 8888:8888 omerozak/econgrowthug-deepnote:v1
# Create docker for EconGrowthUG for use on Deeepnote
FROM condaforge/mambaforge

# updates just in case
RUN apt update

# Create
ENV PROJ_LIB "/opt/conda/share/proj"

# Create environment
RUN conda install mamba -y -c conda-forge --override-channels

# Initialize shell to work with conda
RUN conda init bash

# Install packages
RUN mamba install -y -c conda-forge --override-channels pip georasters geopandas pandas pandas-datareader spatialpandas statsmodels xlrd networkx ipykernel ipyparallel ipython ipython_genutils ipywidgets kiwisolver matplotlib-base matplotlib scikit-image scikit-learn scipy seaborn geoplot geopy geotiff pycountry nb_conda_kernels stata_kernel nltk pygeos plotly nodejs r-dagitty pycountry geocoder camelot-py html5lib ghostscript plotnine ipympl>=0.9.1 git ipumspy dask-geopandas python-kaleido opencv \
  && pip install geonamescache stargazer ipumspy
