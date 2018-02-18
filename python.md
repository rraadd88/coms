# install pkg in editing mode
pip install -e .
or: python setup.py develop

# get version 
pip show pkg

# list all packages installed
pip freeze

# python setup.py sdist

# python -m compileall .

# install all packages from a list at once
pip install -r requirements.txt