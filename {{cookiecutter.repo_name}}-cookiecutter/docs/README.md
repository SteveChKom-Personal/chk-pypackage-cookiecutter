# Documentation
Consider generating documentation using ```sphinx```

A good introduction can be found in </br>
https://samnicholls.net/2016/06/15/how-to-sphinx-readthedocs/. </br>
See official document for detailed documentation


## Current Issues
Relative paths in code snippets such as ```save_load_yaml('./some_file.yml')``` works in source code, 
but does not work with sphinx. </br>

Absolute path is required.  This may mean moving config files to a common folder is a better solution, 
and called via environmental variables is a more systematic solution.
To do this, one could use e.g. ```os.path.expandvars("${ENV_CONFIG_PATH}/some_path/some_file.yml")```.

However, this could lead to resolved paths being visible in the documentation, 
which may not be a good idea.


## Basic setup
```
cd docs
sphinx-quickstart
```
This prompts user to enter a few basic details.
<ul>
<li>Suggests spliting </li>
</ul>

```
cd docs/
sphinx-apidoc -o source/ ../<package>
```
It is important to save the generated rst files to docs/source/.  Otherwise ```py-modindex.html``` will not be generated.

In ```conf.py```, uncomment the following and change the src file path in the ```Path setup``` section.
```
import os
import sys
sys.path.insert(0, os.path.abspath('../../src/'))
```


## Useful configurations
In ```conf.py```, change the following:
```
html_theme = 'sphinx_rtd_theme'
```
which looks much better (and is standard).  ```sphinx-rtd-theme``` may need to be installed manually.

Extensions:</br>
```'sphinx.ext.viewcode'``` - Include source code </br>

## Build
```
cd docs
make html
```


