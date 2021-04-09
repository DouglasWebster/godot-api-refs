# Make links to the Godot API references

This is a small tool to create links to the Godot Help API's and store them as a JSON file in the following format:

```
{
    "animationplayer": "https://docs.godotengine.org/en/stable/classes/class_animationplayer.html", 
    "directionallight": "https://docs.godotengine.org/en/stable/classes/class_directionallight.html", 
    "joint2d": "https://docs.godotengine.org/en/stable/classes/class_joint2d.html",
    "collisionobject2d": "https://docs.godotengine.org/en/stable/classes/class_collisionobject2d.html",
    "physicsbody": "https://docs.godotengine.org/en/stable/classes/class_physicsbody.html",
    "visibilitynotifier2d": "https://docs.godotengine.org/en/stable/classes/class_visibilitynotifier2d.html",
       .
       .
       .
}
```
The Json file can then be used as a list, dictionary etc. to link the Godot class name with its associated help
page on the godot website.

## Prerequisites
The program relies upon the GhApi library and instructions for its installation and use; it will fail to install if the GhApi library is not already installed.  Instruction for the installation of GhApi can be found at https://ghapi.fast.ai


## Installing
You can install the Godot api reference maker package with pip:

``` bash
# On Linux
python3 -m pip install godot-api-refs

# On Windows, if you installed Python 3.7+, you can use:
python -m pip install godot-api-refs
```
I do not have access to a MacOS box so cannot test if it installs and runs OK in that environment.  However, the program is quite simple so it should prove no problem for a standard python environment.
## Running the program

The program can be run using

`python -m godot_api_refs` 
 
This will generate the Godot class links from the stable branch and store them in the file godot_api_calls.json in the current working directory


The progam can be invoked with -h which will give the following output:
```
usage: python -m godot_api_ref [options]

Given a godot-docs branch it scans the class folder and creates a JSON file linking the Godot class name with the API reference

optional arguments:
  -h, --help        show this help message and exit
  --token TOKEN     optional github access token (default "" may only gives 60 reads/hour)
  --branch BRANCH   optional branch for the class files (default: stable)
  -v, --verbose     Set the verbosity level. For example -vv sets verbosity to level 2. Default: 0.
  --check-branches  print out a list of the Godot document branches then exit without making the links
```
The Godot API list can be read from branches other than the stable branch if you require it by using the --branch option (for example `--branch master` will load links to the latest API documentation. )

The option `--check-branches` is an aid to show what branches are available on github; it will print out a simple list then exit.

The option `--token` allows the user to supply an github user token.  This is available in case the user has exhausted their calls to the github api using unauthenticated requests.

The output file will be `godot_api_calls.json` and will be placed in current working directory.






