# Murine Basal Ganglia Notebooks
This repository is a part of the master's thesis *"Graph-based representation, integration, and analysis of neuroscience data &mdash; The case of the murine basal ganglia"*.
In this thesis, we investigate aspects of graph-based data representation in the neuroscience domain. 
The data set basis is a relational database published by Bjerke et al. (2019) of quantitative neuroanatomical data about the healthy rat and mouse basal ganglia ([DOI:10.25493/DYXZ-76U](https://doi.org/10.25493/DYXZ-76U)). This repository contains the relational database as CSV-files, located at `/Data/csvs/basal_ganglia`. The illustration below presents the high-level solution design of the master's thesis. The project's primary notebook converts and inserts the data from these CSV-files into a Neo4j graph database instance. In addition, this project contains notebooks for extending data from external sources and for analyzing the data in the graph model (requires [Neo4j's Graph Data Science Library](https://neo4j.com/docs/graph-data-science/current/)).

<img src="/Data/visualizations/solutiondesign2.png" alt="High-level architecture of the thesis solution" style="width: 400px;"/>

## Getting started
Run the following commands to install the required packages:
```bash
pip3 install -r requirements.txt
python3 setup.py build_ext --inplace
```
All the notebooks use [dotenv](https://pypi.org/project/python-dotenv/) to store connection credentials. The driver connection requires the Neo4j username, password, and bolt URL to run the notebooks.

## Content
Following the solution design, we have separated the different aspects of this project. At the root lies the notebook that creates the graph database from the relational 
(`1. Create the Rodent Basal Ganglia Graph.ipynb`).

The folder `1. Extending the dataset with data from other sources` presents the efforts in collecting data from external sources. Here, we present how we collect data from [NeuroMorpho.Org](http://neuromorpho.org/) and InterLex through the [SciCrunch API](https://scicrunch.org/browse/api-docs/index.html?url=https://scicrunch.org/swagger-docs/swagger.json). For full citation of the downloaded morphologies, see the [neuromorpho data folder README](/Data/csvs/neuromorpho).

The folder `2. Extending the data with extracted information - GraphAnalysis` presents the efforts for running graph algorithms on the data. The notebooks `1. General information search.ipynb` and `1. General information search.ipynb` presents the exploratory data analysis, using the Neo4j Graph Data Science Library and NetworkX, respectively. The notebook `3. UseCases.ipynb` presents the confirmatory data analysis, where we apply analytics to answer specific questions about the data.


## References
I. E. Bjerke et al. "Database of quantitative cellular and subcellular morphological properties from rat and mouse basal ganglia [Data set]".
In: *Human Brain Project Neuroinformatics PlatformØ (2019). DOI: 10.25493/DYXZ-76U.

Giorgio A Ascoli, Duncan E Donohue, and Maryam Halavi. "NeuroMorpho. Org: a central resource for neuronal morphologies". In: *Journal of
Neuroscience* 27.35 (2007), pp. 9247–9251.

FDI Lab - SciCrunch Infrastructure | InterLex | Dashboard. https://scicrunch.org/scicrunch/interlex/dashboard. 
Last accessed: 2020-08-30

