## Common

#### Print Conda version

`conda info`

#### List all installed packages

`conda list`

#### Update any installed program/package

`conda update PACKAGENAME`

#### Update all packages

`conda update -all`

#### Check if tensorflow is installed

`conda list | grep tensorflow`

#### Uninstall Tensorflow

`conda uninstall tensorflow`

#### Show locations of all versionf of Python are currently in the path

`WINDOWS: where python`  
`macOS : which -a python`

## Launch

#### Navigator

`anaconda-navigator`

#### Jupyterlab

`jupyterlab`

## Environments

#### List of all my environments

`conda env list`

#### Create new environment named diao, install Python 3.5

` conda create --name diao python=3.5`

#### Create env from text file

`conda create --file bio-env.txt`

#### Duplicate Env

`conda create --clone diao --name diao-2`

#### Remove env

`conda env remove --name diao`

#### Use/Activate Env

` WINDOWS : activate <envName>`  
` LINUX, macOS : source activate <envname>`

#### Deactivate Env

` WINDOWS : deactivate`  
` macOS : source deactivate`

#### Create Kernel to jupyter notebook from current env

`python -m ipykernel install --user --name <env_name> --display-name "<env_name>"`

#### List All Kernels

`jupyter kernelspec list`

#### Remove Kernel

`jupyter kernelspec remove <kernel-name>`

#### List the history of each change to the current environment

`conda list --revisions`

#### Restore environment to a previous revision

`conda install --revision 2`

#### save env to a text file

`conda list --explicit > blah.txt`

### AI

#### Install tensorflow

`conda install tensorflow or conda install tensorflow-gpu`

#### tensorflow 2.0+ comes with keras

`from keras.layers import Input`  
`from tensorflow.keras.layers import Input`

#### CUDA

`conda list cudatoolkit`

#### CUDNN

`conda list cudnn`

#### Tf and Cuda Version compatible

`https://stackoverflow.com/questions/50622525/which-tensorflow-and-cuda-version-combinations-are-compatible`

### Other useful libraries

```
scikit-learn
scikit-image
pandas
pillow
numpy
```

### Change jupyter lab working directory

```
1. run jupyter notebook --generate-config using cmd
2. goto C:\Users\username\.jupyter\jupyter_notebook_config.py.
3. search for #c.NotebookApp.notebook_dir = ''
4. replace with c.NotebookApp.notebook_dir = 'C:/the/path/to/home/folder/'
Note: Forward slash for dir. Backslash can be used if is in double quote like so
"D:\yourUserName\Any Folder\More Folders\"


### Reference ###
https://docs.conda.io/projects/conda/en/4.6.0/_downloads/52a95608c49671267e40c689e0bc00ca/conda-cheatsheet.pdf
```
