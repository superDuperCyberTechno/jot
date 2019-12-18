# jot
### a CLI for daily journaling

I stumbled upon [jrnl](https://github.com/maebert/jrnl) and thought it was a neat idea so I installed it and tried it. It didn't work very well so I quickly decided to slap something together myself. The result is _jot_.

I've made it as simple as possible: A single executable in non-minified/compiled Python.

### Installation
In order to run _jot_ you need `python3`.
You can download the file and execute it as it is. To make it easy on yourself, you might wanna make it available in your PATH. This can be done like this:

```
cd /usr/local/bin;sudo wget https://raw.githubusercontent.com/superDuperCyberTechno/jot/master/jot && chmod +x jot;cd -;
```

This will download the file into the `/usr/local/bin` folder which should be a part of your PATH already, making it available everywhere in your terminal.

To uninstall:
```
sudo rm /usr/local/bin/jot
```

### Usage
Usage is super simple. Whenever you need to jot something down, simply do the following:
```
jot this is the thing I want to jot down!
```
You have now saved "this is the thing I want to jot down!" as an entry for today!

__Tags__

_jot_ supports tags, using the `-t` option:
```
jot -t=tag1,tag2 this is the thing I want to jot down!
```
This will file "this is the thing I want to jot down!" under both `tag1` and `tag2`. You can have any number of tags defined. Seperate them with a single comma.

__Exporting__

_jot_ keeps track of your entries using a JSON file. This is not very friendly to human eyes, so _jot_ can export your entries for you to read with the `-e` option:
```
jot -e
```
This will export all your entries into a simple TXT file (`~/jot.txt`) so you can peruse them. 

Filter the contents of your exports using tags with the `-t` option:
```
jot -e -t=work,leisure
```
This will only export entries with the `work` or `leisure` tags.

### Technicalities
_jot_ makes use of 3 files when operating:

`~/jot.json` is the data file and contains all your entries in JSON. This is the important file and you want to back it up.

`~/jot.txt` is the parsed data from the file above. This file is non-essential and can be re-generated at will.

`~/.config/jot/jot_config.json` is where _jot_ stores all settings. These can be edited to your liking:

`data_path` will let you define an __absolute__ path where you want _jot_ to save its data (`jot.json` and `jot.txt`). The default is your home folder:
```
"data_path": "/insert/your/own/path/here"
```

`auto_export` forces _jot_ to export the entries every time an entry has been added:
```
"auto_export": true
```
