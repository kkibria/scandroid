# scandroid
Scans english verse in *iambic* and *anapestic* meters. The version 1.1
(2015) source is copied from [Charles O. Hartman's page](https://oak.conncoll.edu/cohar/Programs.htm).

Version 1.1 was written in python 2. I have updated the code for python 3. 
My ultimate goal is to use this for song lyric writing.

## User's Manual
The manual for version 1.1 (pdf) is also copied from Hartman's page to ``doc`` folder. Moving forward,
I will turn the manual into markdown format (work in progress) and be covered under GPL3 so that it can be maintained.  

## Metrical Foot
It is an unit consists of a pattern of stressed and unstress syllables.

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
I use VS code for development and I have multiple versions of python
installed and therefore, point ``pythonPath`` to 
correct python 3 version that has ``wxPython`` installed in it so that ``pylint`` can find ``wxPython``.

```json
{
    "python.linting.pylintArgs": [
        "--extension-pkg-whitelist=wx"
    ],
    "python.pythonPath": "~/AppData/Local/Programs/Python/Python39/python.exe",
}
```