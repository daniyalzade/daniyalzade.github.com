[speakers]: <http://google.com/> 

# PyCode Conf Notes

## Table of Contents
* Topics
* Tools
* [Speakers][speakers]

## Topics

#### PyPy
* In python implementation of the python interpreter
* Faster than cpython on many benchmarks
* Though, limited support for a lot of c-based libraries
* Main speed benefits come from JIT (Just in time optimization) support
* Considering getting rid of the GIL (global interpreter lock), though as of current version there is still a GIL.


### JIT Generator

## Tools
#### virtualenv (python command line utility)
* A way of managing multiple environments at once.
* Especially handy if the different projects you are working on have different library requirements. 
* Works by creating an environment folder for you, and seeting the path to use that folder that has all libraries, etc.

#### zeromq
* A light-weight inner-thread (or process) communication within same/different process on same/different boxes.

#### itty
* itty bitty web framework. (similar to flask)
* easy way of getting a process to respond to HTTP requests

#### Grove
* Hosted easy-to-use IRC for companies. Similar to campfire
* Makes it easy to create groups on the fly (which is burdensome with gchat)

#### Software Transactional Memory
* Way of making concurrency possible without using locking (?)
* Will possibly be used by pypy to remove the GIL in the future

#### pip
* Next generation python package management (easy_install 2.0). Enables installing with source-code, upgrades, removes (which easy_install does not allow)

> pip install --use-mirrors

#### legit
* Github mac client - command line abstraction on main git commands

#### sphinx
* [url] (http://sphinx.pocoo.org/)
* Code documentation markup. Sphinx parser parses this and generates documentaation in HTML/Latex etc.
* There is 

#### bup
* python based filesystem backup tool using github

# sshuttle
* poormans VPN

## Speakers
#### Jesse Noller (Embrace the GIL)
* GIL = Global Interpreter Lock
* GIL is required since the python interpreter is not threadsafe (e.g. reference counting, memory management). This means that no 2 threads could be running at the same time. This limits python to use a single-core at a time.
* GIL is released before IO bound operations.

* Dis module in python

> import dis  
> dis.dis(methodname)  

This would show the bytecode representation of the given method name

* A takeaway is not to run python code in tight-loops, i.e. do not iterate over the same set of instructions very high number of times, since instruction interpretation is very expensive.

#### Raymond Hettinger (what makes python awesome)
* Generators/yield - A way of calling sub-routines back/forth without, and be able to return to a sub-routine where it left off, with full stack-state
s
* with statement - A co-routine that gets exectued before and after the execution of a block of code. Useful for factoring resource management, such as network or files. Also makes it possible to test management portion of the code.

#### Leah Culver (Grove creator)
* backbone.js makes it easy to add a MVC framework into JS code. (sounds like its fairly popular in the audence)

#### Laura Thompson (processing firefox crash reports)
* Sagrada, mozilla message queueing system

Craig Kerstiens (state of python pckg management)
* Don't distribute python packages by hosting them on your server. Does dis-use to the community. 
* Don't depend on external servers for your deployments
* Everyone should use virtualenv & pip (and audience seemed to agree)

Kenneth Reitz: (python for humans)
* [Slides] (https://github.com/kennethreitz/python-for-humans for slides)
* Some standard libraries are broken, e.g. urllib2, subprocess (really hard for beginners to understand)
* Created some libraries that have gotten a lot of adoption in the python community
> * Python requests - httplib for humans
> * Legit - httplib for humans

Avery Pennarun (python is slow only if you use it incorrectly)
* Works at Google in NYC
* Bup - backup software (stores your stuff in git, backup your computer - awesome)
* Uses python to read your filessystem and back it up in git
* Line of code executes x80-100 slower

Learn:
software transactional memory
couroutines
* http://www.dabeaz.com/coroutines/Coroutines.pdf
python 3
* Improvements to GIL
http://www.dabeaz.com/python/GIL.pdf
pypy
* Maybe getting rid of gil
* jit genarator
async python
* twisted/stackless
multitreading
* Process states, ready-wait, iterrupt, OS
mongohub
* http://mongohub.todayclose.com
virtualenv
* For environment management
* http://warm-mist-1692.heroku.com
Smalltalk
* Look at it again
* Presentation with iphone
* ZeroMQ
* poll/select

Jesse Noller:
Slides are @ bitly (put this as well)
Black on white (apple style)

Practicality beats puriy
Use it where it makes sense
Approachability and at the same time maintainability

Embrace the GIL
* dis module
import dis
dis.dis(methodname)

GIL protects (imagine that there is threads running on cores simultaneously)
* Reference count updates
* Mutable types

Python interpreter is not written in a thread-safe manner. It does not use dictionalires in a threadsafe manner, and the refrence counting is not threadsafe. So you cannot run multi threads since it can be preemted


Raymond Hettinger - what makes python awesome?
* Async yield - get around the way of using callbacks (procedural aycn)
* from itty import get, post, run_itty (small web framework)
>> a tiny web service to track a box

* with statement (awesome)
* http://docs.python.org/library/abc.html

leah culver - IRC 
* Grove, IRC server for the company

Alex Gaynor:
* L

Laura Thompson - processing firefox
Sagrada, mozilla queueing system
http://blog.mozilla.com/services/2011/09/15/introducing-project-sagrada/

Craig Kerstiens
State of packaging & Dep mgmt
pypi
pip & virtualenv
pip install --use-mirrors

Kenneth Reitz:
https://github.com/kennethreitz/python-for-humans for slides
Requests
Legit
OXS-GCC Installer
Clint
python requests is good for url opening stuff
http://sphinx.pocoo.org/
http://docs.python-guide.org/en/latest/index.html

Avery Pennarun
Bup - backup software (store your stuff in git, backup your computer - awesome)
VPN software sshuttle
* Tight inner loop is terrible
* Line of code executes x80-100 slower
* You don't want to run a line manytimes.. you just want to interpret once and then execute that really fast in c.. interpretation takes time
* C module is cool
* In python fork using multiple cores
* scipy - puts C code in the python code
* weakrefs - does not increase the reference count


Gary Bernhardt:
http://bret.appspot.com/entry/tornado-web-server
* Flask if you want to add a small http server to an existing application
* python-request to make an easy url call
* http://pypi.python.org/pypi/requests

Dustin Sallings
* Breakdancer
* http://dustin.github.com/2010/10/27/breakdancer.html

Design:
pdf download The Non-Designer's Design Book: Design and Typographic Principles for the Visual Novice

Vagrant - 
* Creating a virtual environment
* Create one for istanbella
http://vagrantup.com/docs/getting-started/index.html

Needle Test Case
* Compare the screenshots for css.. http://needle.readthedocs.org/en/latest/
* How do you run selenium in a headless environment

Pandas:
* Small data data analysis
http://pandas.sourceforge.net/

ipython notebook

Supportig DSLs in Python @pwang

Random random stuff:
* Command two finger swipe up/down, and then you will zoom in

Stackful
*Leak in values into libraries with globals
* 


