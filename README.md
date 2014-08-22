make-chatterbot
===============

By Brandon Jackson

Project started August 2014

make-chatterbot is a simple chatterbot interface that makes it easy to combine the AIML interpreter `pyAIML` with the text-to-speech program `espeak`. At the core of the AI is the open-source, prize-winning A.L.I.C.E. chatterbot. This project began as part of a project to build experiments for the [Kano](http://kano.me) computer.

Installation
------------

- Make sure you have these dependencies installed (see code snippet below for help):
    - the `espeak` package
    - the `pyAIML` Python package 
- Make sure `make-chatterbot.py` is executable
- From the terminal call `./make-chatterbot.py`
- When presented with a prompt, start the conversation!

**Example Installation Procedure (for Unix/Linux with apt-get installed)**

```
git clone https://github.com/brandonjackson/make-chatterbot.git
cd make-chatterbot
sudo apt-get install espeak espeak-data
git clone git://pyaiml.git.sourceforge.net/gitroot/pyaiml/pyaiml
cd pyaiml
sudo python setup.py install
cd ../
sudo rm -R pyaiml
```

Usage
-----

```
usage: make-chatterbot.py [-h] [-m] [-v VOICE] [-p PITCH] [-s SPEED]
                          [-e ENGINE] [-q]
                          [file [file ...]]

A simple chatterbot interface. The program 'learns' conversational rules from
.aiml files, and then allows the user to interact with the chatterbot. By
default the bot's response is output to the espeak text-to-speech (TTS)
engine, although other TTS programs are supported using the -e flag. Custom
aiml files can be loaded using the file positional arguments. If they are
provided then the default AIML file set will not be loaded.

positional arguments:
  file                  custom AIML file (or directory of files) to load

optional arguments:
  -h, --help            show this help message and exit
  -m, --show-matches    show matching patterns that generated the response
  -v VOICE, --voice VOICE
                        name of voice (default=en)
  -p PITCH, --pitch PITCH
                        voice pitch (1-100, default=50)
  -s SPEED, --speed SPEED
                        voice speed in words per minute (default=140)
  -e ENGINE, --engine ENGINE
                        text-to-speech program (default=espeak)
  -q, --quiet           no audio output produced
```

To-Do List
----------

- Move bot predicates to a JSON config file which is stored in the aiml directory so that each bot can have its own name, etc
- Add header with cool ASCII image when first loaded
- Accept a list of AIML files (or a directory of files) to make it easy to load custom intelligences
- Automatically re-build cache when new files detected
- Add command line option to enable a tabula rassa (i.e. disable loading the standard AIML file set)
- Add support for festival TTS engine
- When custom file are provided then save rules to a brain whose name is a hash generated by combining all of the filenames from this batch of customFiles so that if the same files are provided as args then the cache will load automatically. If I do this I will need to add the ability to clear the cache, else development would grind to a halt since aiml files would never reload
- Recursively scan directories passed as a file arg instead of simply using `os.listdir()`, ensuring that subdirectories are loaded too (e.g. enabling a "load all" command by passing `aiml` as an input)


Links
-----

- [pyAIML Homepage](http://pyaiml.sourceforge.net/)
- [eSpeak Homepage](http://espeak.sourceforge.net/)
- [A.L.I.C.E. Homepage](http://alice.pandorabots.com/)
- [Chatterbot Wikipedia Page](http://en.wikipedia.org/wiki/Chatterbot)
- [AIML Wikipedia Page](http://en.wikipedia.org/wiki/AIML)
- [Tutorial that inspired the espeak integration](http://www.iniy.org/?p=68)

Credits
-------

The AIML files in the `standard/` directory are the [A.L.I.C.E. intelligence](http://alice.pandorabots.com/) developed by Richard Wallace, and released under the GNU-GPL license. The files were taken from the "Standard AIML Files" posted [here on SourceForge](http://sourceforge.net/projects/pyaiml/files/Other%20Files/Standard%20AIML%20set/standard-aiml.zip/download) as part of the `pyAIML` package.
