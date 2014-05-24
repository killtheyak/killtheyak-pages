title: Installing IPython Notebooks
updated: 2014-05-23
description: A whip-fast guide to getting started with IPython Notebooks, the best 
persistent-state REPL out there
os: [macosx]
tags: [ipython, bash, notebooks]
deps: [use-virtualenvwrapper]
contributors: ["http://www.github.com/rachelkelly"] 


## After installing virtualenv and virtualenvwrapper

`mkdir IPYTHONENVNAME`  
This can be any environment name you choose.  I call mine `ipy` for  brevity.  IPython has a 
bunch of dependencies and it's nice to have them all in ONE place rather than globally 
throughout your machine.

## pip install  
Once within the environment you name, with (IPYTHONENVNAME) at the beginning of your prompt, 
`pip install` all of the following:  
`jinja2`  
`pyzmq`  
`tornado`  

And finally:  
`ipython`.

Then, to run a local instance of IPython Notebooks, enter `ipython notebook`.  `ipython` is 
the command and `notebook` is the argument.
