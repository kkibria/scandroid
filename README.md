# scandroid
Scans english verse in *iambic* and *anapestic* meters. The version 1.1
(2015) source is copied from [Charles O. Hartman's page](https://oak.conncoll.edu/cohar/Programs.htm).

Version 1.1 was written in python 2. I have updated the code for python 3. 
My ultimate goal is to use this for song lyric writing.

## User's Manual
The manual for [version 1.1](doc/reference/Scandroid_Manual_1-1.pdf) (pdf) from 2015 is copied from Hartman's page to the ``doc/reference`` folder. I have ported the manual to markdown format, so that it will be covered under GPL3 and can be maintained moving forward for future versions. The ported [manual](doc/manual.md) (markdown) is located in the ``doc`` folder. 

## What is Metrical Foot?
It is an unit consists of a pattern of stressed and unstressed syllables.

*Iambic*: Pronounced duh-DUH. Consists of two syllables- an unstressed syllable followed by a 
stressed syllable. An iamb can be made up of one word with two syllables or two different words.

*Trochee*: Pronounced DUH-duh. A line of verse with one or more trochees is said to have a 
trochaic meter. This stress pattern is the opposite of iambic meter.

*Spondee*: Spondees have two stressed syllables, pronounced DUH-DUH.

*Dactyl*: Dactyls are pronounced DUH-duh-duh. This foot has a stressed 
syllable followed by two unstressed syllables.

*Anapest*: Pronounced duh-duh-DUH. Anapestic meter typically divides 
its syllables across multiple words.

## VS code setting

For linting correctly in VS code,
we need to whitelist ``wxPython`` binary package for ``pylint``.

File ``.vscode/settings.json``
```json
{
    "python.linting.pylintArgs": [
        "--extension-pkg-whitelist=wx"
    ],
}
```

I use VS code for development and I have multiple versions of python
installed and therefore, point ``pythonPath`` to 
correct python 3 version that has ``wxPython`` installed in it so that ``pylint`` can find ``wxPython``.

File ``.vscode/settings.json``
```json
{
    "python.pythonPath": "~/AppData/Local/Programs/Python/Python39/python.exe",
}
```

> You can also interactively select python version in VS code status bar.

Following are the instruction for running scandroid from source and buuilding executable binary
in windows. 

## Running Scandroid in windows
Of course you have to have Python 3 installed. I have tested with Python 3.7.3.
You also need `wx` installed for the user interface.

```
pip install -U wxPython
```
Now you should be able to run the source directly using python interpreter from cloned scandroid directory.
```
py ./source/Scandroid.py
```

## Building executable in windows
Building executable can be a preferred option since excutable won't need a machine with python installed.
You can distribute just the exceutable bundle. The bundle will have everything it needs to run.
If you can run scandroid successfully, you can use `pyinstaller` to build executable for your o/s.
First install PyInstaller.
```
pip install pyinstaller
```
Now you should be able to build the executable from cloned scandroid directory.

### build with one file option
This option is useful for easy distribution. Run PyInstaller with `-F` option,

```
pyinstaller -F --add-data "./source/scandictionary.txt;." "./source/Scandroid.py"
```
This will generate a single executable file in a subdirectory called `dist`. You simply distribute
this executable.

### build with one folder option
This option is useful for debugging a bundle. Run PyInstaller with `-D` option,

```
pyinstaller -D --add-data "./source/scandictionary.txt;." "./source/Scandroid.py"
```
This will generate the executable bundle folder in a subdirectory called `dist`. You can zip
the bundle folder inside `dist` and distribute.

There are other advanced options available for building. 
For more details, see the [pyinstaller manual](https://pyinstaller.readthedocs.io/).

> PyInstaller is not a cross platform builder. That means if you want to build a Mac
> executable, you have to build the executable in a Mac. I have built and tested it only in an
> windows 10 machine.

## MacOs and ubuntu
Building binary For all platforms consult `.github/workflows` folder.
This floder contains commands for building binaries using github actions. We use github actions
to build binaries for windows, MacOs and ubuntu each time we do a commit and release. You can download
the prebuilt binaries from [Releases](../../releases).
