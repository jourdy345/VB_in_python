# Virtualenvwrapper quick start
- Run: `workon`  
A list of environments, empty, is printed.  
- Run: `mkvirtualenv temp`  
A new environment, `temp` is created and activated.  
- Run: `workon`  
This time, the `temp` environment is included.  
- Run: `deactivate`  
This will deactivate the virtual environment that is currently running.

# How to install virtualenvwrapper
- Make sure you have installed `virtualenv`.  
  `$ sudo pip install virtualenv`
- Now install `virtualenvwrapper`.  
  `$ sudo pip install virtualenvwrapper`.
- These two are the only libraries that should be installed globally. Other libraries will be installed inside the local environment of `virtualenv`. That's what it's made for!  
- After installing both libraries, we should add three lines to our shell startup file (mine is `.bash_profile` but it may vary depending on your computer OS.). Add the following:

```bash
export WORKON_HOME=$HOME/.virtualenvs
export PROJECT_HOME=$HOME/Devel
source /usr/local/bin/virtualenvwrapper.sh
```
-----------------
### TIP
- If you are not familiar with shell files, you can do what I do whenever I have to change any configuration. First, use the `vim` editor like this: `vim ~/.bash_profile`. This will open up the `vim` editor for you.
- You can't just start writing after you've arrived at the `vim` editor. Tap `a` which stands for `append` and the editor will give you this sign: `-- INSERT --`. This means you can start editing. Add the content above. Again, you can't just quit. You should press `esc` and the `-- INSERT --` sign will disappear. This means you are finished with editing the file.
- To exit the `vim` editor, press `:wq`, which stands for 'write and quit'. If you press `:q`, it means just quit. This will override any change that you have made to the file.

----------

- If you're done editing, we should restart the configuration.

```bash
source ~/.bash_profile
```
- Now you're done! Enjoy coding!

# Basic Usage
1. Create a virtual environment:  
```
$ mkvirtualenv venv
```
2. Work on a virtual environment:  
```
$ workon venv
```
3. Or you can make a project. This creates both the virual environment and a project directory inside `$ PROJECT_HOME`, which is `cd`-ed into when you `workon myproject`.  
```
$ mkproject myproject
```
4. `workon` deactivates the current environment and swiches into another.
5. To deactivate, `deactivate`.
6. To delete:  
```
$ rmvirtualenv venv
```
7. In order to keep your environment consistent, it's a good idea to ''freeze'' the current state of the environment packages. To do this, run

```
$ pip freeze > requirements.txt
```
This will create a requirements.txt file, which contains a simple list of all the packages in the current environment, and their respective versions. You can see the list of installed packages without the requirements format using “pip list”. Later it will be easier for a different developer (or you, if you need to re-create the environment) to install the same packages using the same versions:

```
$ pip install -r requirements.txt
```
Lastly, remember to exclude the virtual environment folder from source control by adding it to the ignore list, for example, `.gitignore`.
  
# autoenv
(Only for Mac users) When you `cd` into a directory containing a `.env`, `autoenv` automatically activates the environment. You can install it with `brew`:

```
$ brew install autoenv
```

For Linux:  

```
$ git clone git://github.com/kennethreitz/autoenv.git ~/.autoenv
$ echo 'source ~/.autoenv/activate.sh' >> ~/.bashrc
```

