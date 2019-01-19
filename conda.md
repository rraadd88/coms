## create venv   

    conda create --name test python=3.6 biopython
    source activate test
    source deactivate
    conda info --envs

## current venv

    conda list 

## grep

    conda list -n test

## export and install

    conda env export | grep -v "^prefix: " > imaging.yml

    conda env create -f environment.yml

    conda env create --force -f 1_dms.yml

## delete env  

    conda env remove --name name

## clone (copy) env

    conda create --name myclone --clone myenv

## rename env

    conda create --name new_name --clone old_name

    conda remove --name old_name --all # or its alias: `conda env remove --name old_name`

## export all envs datewise

    #!/bin/bash

    NOW=$(date "+%y_%m_%d")
    mkdir -p envs-$NOW
    ENVS=$(conda env list | grep '^\w' | cut -d' ' -f1)
    for env in $ENVS; do
        source activate $env
        conda env export | grep -v "^prefix: " > envs-$NOW/$env.yml
        echo "Exporting $env"
    done

## export all envs namewise

    #!/bin/bash

    mkdir -p envs
    ENVS=$(conda env list | grep '^\w' | cut -d' ' -f1)
    for env in $ENVS; do
        source activate $env
        conda env export | grep -v "^prefix: " > envs/$env.yml
        echo "Exporting $env"
    done
