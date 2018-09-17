# Awesome Python VS Code
I've been using Visual Studio Code since [before](https://github.com/DonJayamanne/pythonVSCode) the python extension was supported by Microsoft.  Now a Microsoft project, the [Python Extension for Visual Studio Code](https://github.com/Microsoft/vscode-python) has become even more featureful featuring their own [remote debugging](https://github.com/Microsoft/ptvsd) tool and their own auto-completion and analysis engine through the new [Language Server Protocol](https://microsoft.github.io/language-server-protocol/).

# My Extensions 
* [:emojisense:](https://marketplace.visualstudio.com/items?itemName=bierner.emojisense)
* [.gitignore Generator](https://marketplace.visualstudio.com/items?itemName=piotrpalarz.vscode-gitignore-generator)
* [Better TOML](https://marketplace.visualstudio.com/items?itemName=bungcip.better-toml)
* [Bracket Pair Colorizer](https://marketplace.visualstudio.com/items?itemName=CoenraadS.bracket-pair-colorizer)
* [Docker](https://marketplace.visualstudio.com/items?itemName=PeterJausovec.vscode-docker)
* [Enki](https://marketplace.visualstudio.com/items?itemName=enkia.enki-vscode-theme) - Theme
* [Git Blame](https://marketplace.visualstudio.com/items?itemName=waderyan.gitblame)
* [hide-gitignored](https://marketplace.visualstudio.com/items?itemName=npxms.hide-gitignored)
* [Indent Rainbow](https://marketplace.visualstudio.com/items?itemName=oderwat.indent-rainbow)
* [Path Intellisense](https://marketplace.visualstudio.com/items?itemName=christian-kohler.path-intellisense)
* [Polacode](https://marketplace.visualstudio.com/items?itemName=pnp.polacode)
* [Prettier](https://marketplace.visualstudio.com/items?itemName=esbenp.prettier-vscode)
* [Rainbow CSV](https://marketplace.visualstudio.com/items?itemName=mechatroner.rainbow-csv)
* [Smooth Type](https://marketplace.visualstudio.com/items?itemName=spikespaz.vscode-smoothtype)
* [VS Live Share](https://marketplace.visualstudio.com/items?itemName=MS-vsliveshare.vsliveshare)
* [VS Live Share Audio](https://marketplace.visualstudio.com/items?itemName=MS-vsliveshare.vsliveshare-audio)
* [vsvode-python-docstring](https://marketplace.visualstudio.com/items?itemName=azaugg.vscode-python-docstring)
* [Python](https://marketplace.visualstudio.com/items?itemName=ms-python.python)

# My configuration
```json
{
    "python.formatting.provider": "black",
    "workbench.colorTheme": "Enki - Night Owl",
    "python.unitTest.pyTestEnabled": true,
    "editor.minimap.enabled": false,
    "editor.formatOnSave": true,
    "editor.formatOnPaste": false,
    "editor.formatOnType": false,
    "[html]": {
        "editor.formatOnSave": false
    },
    "python.autoComplete.showAdvancedMembers": true,
    "python.autoComplete.addBrackets": true,
    "workbench.iconTheme": "enki",
    "editor.cursorBlinking": "expand",
    "editor.renderWhitespace": "boundary",
    "editor.formatOnSaveTimeout": 1500,
    "python.formatting.blackPath": "/Users/erin/.pyenv/versions/3.7.0/bin/black",
    "python.formatting.blackArgs": [
        "--skip-string-normalization",
        "--line-length",
        "99"
    ],
    "python.jediEnabled": false,
    "prettier.tabWidth": 4,
    "docker.attachShellCommand.linuxContainer": "/bin/bash"
}
```
I usually have project specific configurations too.  These are usually things like linting, the python path that pipenv created, and sometimes black arguments.  My configuration file used to be a lot longer, but the python extnesion has made more settings I had specified deafaults, a feature I like.  It works out of the box, these things just make it better.

# The Python Langauge Server
The [Python Language Server](https://github.com/Microsoft/python-language-server) is a new alternative to packages like [Jedi](https://github.com/davidhalter/jedi). So far I am having a positive experience with this.  I just recently switched from Jedi to the languge server.  To do that you have to disable Jedi by setting `python.jedienabled` to false.  The language server will be downloaded and run.  You can enable or disable this per a project.  I've seen some speed improvments in autocomplete, and better detection for inherited properties and methods when working with Django models.

# Pipenv Support
 Out of the box the Python extension supports [conda](https://conda.io/),
  [direnv](https://direnv.net/),
  [pipenv](https://pypi.org/project/pipenv/),
  [pyenv](https://github.com/pyenv/pyenv),
  [venv](https://docs.python.org/3/library/venv.html#module-venv),
  [virtualenv](https://pypi.org/project/virtualenv/).  Pipenv is the one I choose to use.  When I open a project that has a pipfile, visual studio code automatically picks up on the virutalenv to use when running Jedi, or it's own analysis engine against my code base.  If you install any dependecies like [rope](https://github.com/python-rope/rope) for refactoring, [ptvsd](https://github.com/Microsoft/ptvsd/) for remote debugging, [mypy](https://github.com/python/mypy), [pylint](https://github.com/PyCQA/pylint) for linting, or [black](https://github.com/ambv/black) for formatting through visual studio code, they automatically get added to your Pipfile.  When you run code, it uses the virtualenv created by pipenv to do all of it's business.  It just knows about it, it's magical! 
 
# Black Support
I love using the code formatter [Black](https://github.com/ambv/black).  Visual studio code supports black out of the box, along with [autopep8](https://github.com/hhatto/autopep8), and [yapf](https://github.com/google/yapf).  You can see above that I have some black arguments applied by default, with the editor set to format on save.  This keeps all of my code nice a tidy, while minimizing diffs.
 
# Debugging Support
Visual Studio Code supports debugging for a lot of different project types.
  [Django](https://pypi.org/project/Django/),
  [Flask](https://pypi.org/project/Flask/),
  [gevent](https://pypi.org/project/gevent/),
  [Jinja](https://pypi.org/project/Jinja/),
  [Pyramid](https://pypi.org/project/pyramid/),
  [PySpark](https://pypi.org/project/pyspark/),
  [Scrapy](https://pypi.org/project/Scrapy/),
  [Watson](https://pypi.org/project/Watson/)
  are all supported.  I can really only speak to the Django and Flask debugging which are FANTASTIC.  The debugger will automatically run the server using `manage.py` or `flask run` and attach itself letting you set breakboints and logpoints, even from the jinja or html templates!  I'm working on another post where I detail how to do remote debugging using [ptvsd](https://github.com/Microsoft/ptvsd/) and docker for Django apps.
  
# PyTest Support
When you open up a file with pytest tests in it, you will be able to run individual tests right from the editor.  Sure you could run `pipenv run pytest -k NAME_OF_TEST` but that's so boring, just have Visual Studio Code do it for you!
  
# Docker Support
I am sure that I am not using this to it's full potential.  It's great to get a quick overview of my containers, which ones are stopped and which are running. It's also great that I can right click on any running container and attatch a shell to it.  You'll notice in my configuration that I have my default command as `/bin/bash` instead of the default of `/bin/sh` when attaching a shell. 
  
 # Built in terminal emulator
As [Kenneth Reitz](https://github.com/kennethreitz) mentioned in his [post](https://www.kennethreitz.org/essays/why-you-should-use-vs-code-if-youre-a-python-developer), the built in terminal emualtor is fantastic.  It uses the same engine as [Hyper](https://hyper.is/). I love not having to open another window to run commands.
  
# Git Support
There is fantasic git support built into the editor.  Besides a gitignore plugin, and a gitblame plugin, all of the stuff you'd expect to be in a plugin like git gutter are built into the editor.  You can also stage, commit, push, pull, checkout, etc all through the git tab.

# Key Bindings for pretty much any editor ever
If you don't want to move away from your editor because you don't want to learn a bunch of new keyboard shortcuts and bindings, fear not; there are key binding extensions for pretty much every editor out there.  Want to use vim?  [Go for it](https://marketplace.visualstudio.com/items?itemName=vscodevim.vim).  How about spacemacs? [Yup](https://github.com/VSpaceCode/VSpaceCode).  Coming from Sublime Text?  Well you'll probably want [this](https://marketplace.visualstudio.com/items?itemName=ms-vscode.sublime-keybindings).  Switching has never been easier!

# In Conclusion
VS Code with the Python exnteion has been my daily driver for over two years.  It's only gotten better with time.  If you were thinking of making the switch, there has never been a better time!  If you already use it, I hope you have enjoyed my setup.  
