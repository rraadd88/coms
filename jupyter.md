## jupyterlab keyboard shortcut to move cells

    {"shortcuts": [
            {
                "command": "notebook:move-cell-up",
                "keys": [
                    "Alt ArrowUp"
                ],
                "selector": ".jp-Notebook:focus"
            },  
            {
                "command": "notebook:move-cell-down",
                "keys": [
                    "Alt ArrowDown"
                ],
                "selector": ".jp-Notebook:focus"
            },  
        ]
    }
    
## grep all `ipynb`s in subdirectories

    find . -name "*.ipynb" | xargs nbgrep "heatmap"
    
## Start the IPython kernel on the server with the following options:

    ipython notebook --no-browser --port=7000

## Set up a ssh connection to the server on your local machine with the following options:

    ssh -N -f -L localhost:7000:localhost:7000 name@192.168.XX.XX

## through server

    ssh -NfL 8888:localhost:8888 machineA.com ssh -NfL 8888:localhost:8888 machineB.com

## Now you can access the notebook by directing your browser to:

    localhost:7000

## You can check the host from the notebook by typing:

    import socket
    socket.gethostname()

## one jupyter session multiple environments

    source activate gen
    conda install ipykernel
    python -m ipykernel install --user --name gen
    
    ENVS=$(conda env list | grep '^\w' | cut -d' ' -f1)
    for env in $ENVS; do
        source activate $env
        python -m ipykernel install --user --name $env
        echo "$env"
    done
    
## change font 
 
    from IPython.core.display import HTML
    HTML("""
    <style>
    div.output_area pre {
        font-family: Consolas, monospace;
    font-size: small;
    }
    table.dataframe {
        font-family: Monaco;
    }
    </style>
    """)

## enable tqdm in jupyterlab
    #usual installation 
    pip install ipywidgets 
    jupyter nbextension enable --py widgetsnbextension
    #you are my saver!
    jupyter labextension install @jupyter-widgets/jupyterlab-manager    
