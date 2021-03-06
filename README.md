# Misc
Miscellaneous Code, see https://github.com/adam-p/markdown-here/wiki/Markdown-Cheatsheet for a Github markdown cheatsheet 

## Line by Line Profiling of Python Code
https://github.com/pyutils/line_profiler#id2

## Pycharm marking modules as "Cannot find reference '<module>' in '__init__.py'"
In Pycharm go File - Invalidate Caches/Restart - Invalidate and Restart from [comment here](https://stackoverflow.com/a/20479761)

## Merging Github Repos
See [MergingRepos](MergingRepos.MD) for how to merge Github repos (especially those owned by others) with your own code.

## UbuntuSetup.txt
See [UbuntuSetup](UbuntuSetup.MD) for setting up a new Ubuntu install and some desired programs. Use in combination with [this readme](https://github.com/BraunPenguin/InstanceSegmentation-Detectron2/Readme.MD) for Instance Segmentation.

## ChromeDarkTheme
Simply Dark Chrome Theme

Add to chrome by downloading, going to chrome://extensions, enable developer mode, then drag and drop the .crx file into chrome. Instructions source: https://blog.hunter.io/how-to-install-a-chrome-extension-without-using-the-chrome-web-store-31902c780034

## Green With Envy
Nvidia graphics monitor and overclocking utility for Ubuntu from https://gitlab.com/leinardi/gwe. See [UbuntuSetup](UbuntuSetup.MD) for installation/use info.

## Setting up Github with MATLAB
See [MATLABwithGithub](MATLABwithGithub.MD) for how to setup Github in MATLAB

## Moving Virtual Environments in Pycharm
After moving the venv folder:
- Go to venv/bin/, open the activate file, and edit the VIRTUAL_ENV variable line to the new path.
- Also in venv/bin/, open all the pip files, and edit the top line to match the new path. 
