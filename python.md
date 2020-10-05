## 2to3 
    
    2to3 -w BAGEL.py

## repair scripts (tabs and spaces)
    
    autopep8 -i BAGEL.py
    
## install pkg in editing mode
    pip install -e .
    or: python setup.py develop

## get version 
    pip show pkg

## list all packages installed
    pip freeze

## python setup.py sdist

    python -m compileall .

## install all packages from a list at once
    pip install -r requirements.txt

# Troubleshoot: SSL errors, certificate invalid  
    pip install --trusted-host pypi.org --trusted-host files.pythonhosted.org package  

# Increasing code performance through caching decorator, which wraps a function with a memoizing callable that saves up to the maxsize most recent calls (default: 128).

    @lru_cache()
    def function():
