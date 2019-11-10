# python-reference

#### package backup with pip
`env1/pip freeze > requirements.txt`<br>
`env1/pip install -r requirements.txt`

#### package backup with conda
`source activate condaEnv`<br>
`conda env export > environment.yml`<br>
`conda env create -f environment.yml`

#### find location of conda environment
`where python` or `which python`

#### Ubuntu terminal ssh connection
`ssh -X vbajenaru3@buffet01.cc.gatech.edu`

#### Ubuntu Nautilus file connection
`sftp://vbajenaru3@buffet01.cc.gatech.edu/home/vbajenaru3/`

#### To be able to see kernel in jupyter-notebook.  Make sure to restart after these changes:

`pip install --user ipykernel`<br>
`python -m ipykernel install --user --name=CS6475`

#### To be able to see kernel in jupyter-lab.  Make sure to restart after these changes:

`source activate CS6475`<br>
`conda install ipykernel`<br>
`ipython kernel install --user --name=CS6475_jup_lab`<br>
`conda deactivate`

#### Default Anaconda channels
`defaults`<br>
`conda-forge`<br>
`https://pypi.python.org/`<br>
`https://repo.continuum.io/`<br>
`https://pypi.python.org/simple`<br>
`https://pypi.python.org/pypi`<br>

#### check current python environment information
`import platform`<br>
`print('architecture:', platform.architecture())`<br>
`print('python_version:', platform.python_version())`<br>
` `<br>
`import wheel.pep425tags`<br>
`import pprint`<br>
`print('-wheel.pep425tags.get_supported:')`<br>
`pprint.pprint(wheel.pep425tags.get_supported())`<br>

#### install package with setup.py
`pip install .`

#### install .whl package
`pip install test.whl`
