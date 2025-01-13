
# CNA-Modules

Official code for the paper *Graph Neural Networks Need Cluster-Normalize-Activate Modules* accepted at NeurIPS 2024.

[![NeurIPS 2024 Poster](https://img.shields.io/badge/NeurIPS%202024-Poster-blue)](https://neurips.cc/virtual/2024/poster/94196)

[![arXiv](https://img.shields.io/badge/arXiv-2412.04064-b31b1b)](https://arxiv.org/abs/2412.04064)


![alt text](images/cna_robots.png "CNA-Modules")

## Installation
### Dockerfile
We provide a `Dockerfile` for ease of reproducibility. See the Docker Docs on [How to get started](https://docs.docker.com/guides/get-started/).

### Via installation script
Navigate into the directory `cna_modules`.
Then execute following command to make the script executable:
```bash
chmod +x install_script.sh
```

After that execute the script via:
```bash
bash -i install_script.sh
```

When the script executed successfully, activate the conda environment via:
```bash
conda activate cluster-normalize-activate
```

### Via conda environment
To install the necessary libraries, you can create a conda environment using the following command:

```
conda env create -f environment.yml
```

The required libraries are saved in the `environment.yml` file. After the installation is complete, activate the environment with the following command:

```
conda activate cna-modules
```

Alternatively, you can run the following command to install:

```
make install
```

## Project Structure

The Python scripts can be found in the `src` directory, and the figures are located in the `images` directory.

## Usage

To use the project, navigate to the `~/cna_modules/src` directory and run the appropriate script.

```
python scripts/execute_experiments.py
```

To adapt the parameters open the file `model_params.py` in the `utils` directory, 
and you can here see the possible options to chose or adapt:

```
experiment_number = ...  # number of experiment
epochs = [...]  # number of epochs (list)
model_type = ...  # to define the model type
num_hidden_features = [...]  # number of hidden features (list)
lr_model = [...]  # learning rate for the model (list)
lr_activation = [...]  # learning rate for the activations (list)
weight_decay = [...]  # weight decay for both (list)
clusters = [...]  # number of clusters (list)
num_layers = [...]  # number of layers (list)
num_activation = [...]  # number of activations inside RPM (list)
n = ...  # numerator
m = ...  # denominator
recluster_option = ...
activation_type = [...]  # activation type (list)
mode = [...]  # distance metric type (list)
with_clusters = [...]  # flag for clustering (list)
use_coefficients = ...  # flag for use of coefficients in our Rationals
device = torch.device("cuda" if torch.cuda.is_available() else "cpu")
# Types: Planetoid, CitationFull, Amazon, WikipediaNetwork, WebKB
# name of the dataset (Cora, CiteSeer, PubMed, Cora_ML, chameleon, Photo etc.)
set_dataset = ...  # here to set the dataset
task_type = ...  # here to set the task type
```

But you can also use the predefined configurations as listed in the directory `utlis/configs`. 
For executing an experiment through this way you can run:
```
python scripts/execute_experiments.py --config [name of configuration] --num_seeds [num of seeds]
```
An excerpt from all accessible configurations: 

CiteSeer (Node Classification):
```text
citeseer_4_gatconv 
citeseer_2_gcnconv
citeseer_4_gcnconv 
citeseer_8_gcnconv 
citeseer_16_gcnconv
citeseer_32_gcnconv
citeseer_64_gcnconv 
```
Cora (Node Classification):
```text
cora_4_sageconv
cora_2_gcnconv 
cora_4_gcnconv 
cora_8_gcnconv
cora_16_gcnconv
cora_32_gcnconv 
cora_64_gcnconv
cora_96_gcnconv 
corafull_2_transformerconv
```
Others (Node Classification):
```text
squirrel_2_dirgcnconv
computers_2_transformerconv
chameleon_2_dirgcnconv 
texas_2_sageconv 
wisconsin_2_transformerconv 
dblp_4_transformerconv 
photo_4_transformerconv
pubmed_2_transformerconv
```
Ogbn-arxiv (Node Property Prediction):
```text
ogbn-arxiv_4_nodeproppred_sageconv 
ogbn-arxiv_4_nodeproppred_gcnconv 
```
Others (Node Regression):
```text
chameleon_2_node_regression_transformerconv 
squirrel_2_node_regression_transformerconv
``` 
We ask you kindly to have a look at `src/utils/configs/` to explore other options.



## Contributors

- [Arseny Skryagin](https://github.com/askrix/), [Felix Divo](https://felix.divo.link/), [Amin Ali](https://github.com/MAminAli) 

## How to cite
```latex
@inproceedings{Skryagin_Graph_Neural_Networks_2024,
    author = {Skryagin, Arseny and Divo, Felix and Ali, Mohammad Amin and Dhami, Devendra Singh and Kersting, Kristian},
    month = dec,
    series = {The Thirty-eighth Annual Conference on Neural Information Processing Systems},
    title = {{Graph Neural Networks Need Cluster-Normalize-Activate Modules}},
    url = {https://openreview.net/forum?id=faj2EBhdHC},
    year = {2024}
}
```



## License

This project is licensed under the MIT License - see the LICENSE file for details.
