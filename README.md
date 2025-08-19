# VIBTOBIlab.github.io
Overview and documentation of TOBI GitHub repositories.

## Run website locally
- Install Jekyll requirements
- Install webpage dependencies: `bundle install`
- Run Jekyll web server: `bundle exec jekyll serve`
- The website is now hosted at ...

### Folder structure
Requires the following folder structure for projects:
```
pages/
|-- sample_project/
    |-- sample_project.md
    |-- wiki/
        |-- sample_wikipage.md
        |-- sample_wikipage2.md
```
where every GitHub repository has one folder with in its root the README file
and a subfolder containing all wiki pages of that repository.


### Jekyll file headers
The project markdown files need to contain the following items in their header:

#### README file
```
---
name: "simple"
description: "A simple tool"
layout: default
tags: project_home, simple
permalink: /projects/simple
project: simple
github_project: "https://github.com/VIBTOBIlab/simple"
---
```

#### Wiki page
```
---
name: docs
title: docs
layout: default
permalink: "/projects/simple/wiki/docs"
tags: wiki, simple
project: simple
github_project: https://github.com/VIBTOBIlab/simple
---
```

## Jenkins post-build Groovy script
NOT SURE WE NEED THIS
```
def projectName = manager.build.project.name
 
// replace with command of your choice for OS of your choice
def processBuilder=new ProcessBuilder('/home/compomics/miniconda3/bin/python', 'generate_docs.py', '-c', 'generate_docs_token.yaml', '-u', 'compomics', '-p', projectName, '-g')
manager.listener.logger.println(processBuilder.command())
processBuilder.redirectErrorStream(true)
processBuilder.directory(new File('/home/compomics/compomics.github.io'))
def process = processBuilder.start()

process.inputStream.eachLine {manager.listener.logger.println it}
```

## Created with
- Jekyll template [Boostrap 4 Github Pages](https://nicolas-van.github.io/bootstrap-4-github-pages/).
- Bootstrap 4
- Font Awesome 4.7.0
- ...