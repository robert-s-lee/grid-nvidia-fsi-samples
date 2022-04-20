
Grid.ai example of Nvidia [fsi-samples](https://github.com/NVIDIA/fsi-samples)

 Other Grid.ai NVIDIA examples:
- Grid.ai NVIDIA [DALI](https://github.com/robert-s-lee/grid-nvidia-dali)
- Grid.ai NVIDIA [fsi-samples](https://github.com/robert-s-lee/grid-nvidia-fsi-samples)

# prerequisites

- setup conda and Jupyter kernel profile 
```bash
export CONDA_NAME=tabformer
conda create --yes --name $CONDA_NAME python=3.8
conda activate $CONDA_NAME # note you may get prompt to run `conda init bash && exit`
pip install ipykernel # allow usage with Jupyter notebook
python -m ipykernel install --user --name=$CONDA_NAME # show conda env in Jupyter notebook
ipython profile create
```
- aws cli
```bash
curl "https://awscli.amazonaws.com/awscli-exe-linux-x86_64.zip" -o "awscliv2.zip"
unzip awscliv2.zip
sudo ./aws/install
rm -rf aws
```

- install RAPIDS
[cudf](https://github.com/rapidsai/cudf) cannot be install with pip
below is from [RAPIDS Release Picker](https://rapids.ai/start.html#get-rapids)

run nvcc to get cudatooklit
python 3.8 grid lightinign 

```bash
conda create -c rapidsai -c nvidia -c conda-forge \
    rapids=22.04 python=3.8 cudatoolkit=11.0 dask-sql
```    

- install other python libraries
```bash

pip install -r https://raw.githubusercontent.com/NVIDIA/fsi-samples/fraud_detection/fraud_detection/requirements.txt
pip install -r https://raw.githubusercontent.com/NVIDIA/fsi-samples/fraud_detection/fraud_detection/TabFormer/GNN_XGB/requirements.txt
```

- get the model

```bash
git clone https://github.com/NVIDIA/fsi-samples
cd fsi-samples
git branch -a
git checkout fraud_detection
cd fraud_detection/TabFormer/GNN_XGB
```

- get the data

```bash
mkdir basedir
cd basedir
mkdir data
cd data

aws --no-sign-request s3 cp s3://gridai-tabformer/data.tar.gz .
gzip -dc data.tar.gz | tar -xvf -
```

# Jupyter notebook




