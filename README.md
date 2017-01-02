# ibnr-conf
This is the config file that is consumed by ibnr's install script.

## Format
  ### Sample Entry
  `nemo			    nemo			   ppa:webupd8team/nemo3		 b	0:0:0 "http://www.webupd8.org/2016/11/nemo-320-with-unity-patches-and-without.html"`  
  There are 6 columns in this file. Each column *should* hold a value or have ! to indicate no value.
  1. Program Name - This is the casual program name given to identify the software.
  2. Actual Program Name - This is the program name with which it will be installed as passed to `apt`.
  3. PPA - The PPA for the software.
  4. Type of Install/TOI - Type of install. This could be b for basic, dev for dev, g for games etc. This option is the same as that passed to the `--type` argument to the install script.
  5. Properties - Colon (:) separated tuple, that identifies the following properties for the entry,
	 1. First flag - if 1, indicates that there is a separate script for installing this software identified by the name - `<column2_entry>-install.sh`. The install script looks for a file with this name to be run inside the [install_scripts](https://github.com/wrvenkat/install_scripts) directory. If the PPA entry is not !, then the PPA is added before the script is run. If the value is 0, then indicates that it needs to be installed using apt.
	 2. Second flag - when the value is 1, this entry is a dependency for the entry above and is processed first before the entry above is processed. There can be as many dependency entries as required. Hence, software and their dependencies should be moved around together. If the value is 0, then it is a standalone entry.
	 3. Third flag - when this flag is 1, it indicates, the entry here needs to be installed as part of a dist-upgrade after an update rather than as an install.
  6. Comments - This column holds any text within double quotes that can be left behind as a sort of help message that can be referred to for further information. The text within the double quotes is taken literally and hence preserves neew-lines too. Any double-quotes present as part of the text needs to be escaped with a backslash. 
  
  Generally, any text enclosed within double quotes are taken literally.

## Getting Started
  * All column values should either have an entry or have ! as a place holder value.
  * This file contains stable version organized along the line of Ubuntu's version number (14.04, 16.04). All enabled entries in a particular version have been tested on that version of Ubuntu.
  * Any part of a line starting with a # is considered as a comment and is ignored. So, if you don't need a software to be installed, you can simply disable it by commenting it out.
  * The install script checks whether a PPA already exists or not before adding it.
  * If you want to contribute, you can do so by contributing entries alone or if the installation requires a script, the entry and the corresponding install script. For more information on this, please see [install_scripts](https://github.com/wrvenkat/install_scripts).

## LICENSE

[GNU GPLv3](https://www.gnu.org/licenses/gpl-3.0.en.html)
