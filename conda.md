#create venv
conda create --name test python=3.6 biopython
source activate test
source deactivate
conda info --envs

#current venv
conda list 

#grep
conda list -n test

# export and install
conda env export | grep -v "^prefix: " > imaging.yml

conda env create -f environment.yml

conda env create --force -f 1_dms.yml

#if error

conda env remove --name 1_dms

# rename env

conda create --name new_name --clone old_name
conda remove --name old_name --all # or its alias: `conda env remove --name old_name`