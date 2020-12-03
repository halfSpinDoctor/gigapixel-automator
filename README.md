# gigapixel-automator
Command line automation for TopazAI Gigapixel for macOS

Written with AppleScript, and uses the System Events application to send menu commands and button commands to the UI

## Introdution
Currently tested and working for Gigapixel AI v4.1.2 on macOS 10.12 Sierra and 10.13 High Sierra. Verified that this does NOT work for the latest release of Topaz Gigapixel AI, which uses a secondary popup screen for setting the output directory and vastly different UI.

This works by driving the UI of Gigapixel AI, so the application needs to be open and se

## Installation
Download the gigapixel-automator file, put it in a location on the path, then make it execuatable (chmod a+x gigapixel-automator)

## Usage
Before calling the automator from the command line, start the Topaz Gigapixel AI application and get all of the settings you would like to use for the batch set up first. E.g. Resize By [Scale | Width | Heigh], supress noise level, remove blur level, output prefix/suffix, ...

*Note*: You *must* select the "Save To > Custom Folder" option in the OUTPUT section of the UI, or the automation will fail.

`gigapixel-automator <full path to input directory> <full path to output directory>`

The automator will then invoke the "File > Open Images ..." menu, go to the specified input directory, and select all valid images in that directory.

After the images load into the Gigapixel UI, it will select the "Browse..." button on the UI, select the output file, then start processing. The 

*Notes*:
* Input and output directory must be a full path to the directory. Use $PWD to make the path relative to the current working directory.
* You can use the backslash escape character for spaces and special characters as usual (i.e. any path that auto-completes in bash /should/ work)
* The command will wait to return control to the command prompt until processing is complete. This enables batch processing over multiple directories.
* If you use Ctrl+C to kill the command, it will not stop processing in Gigapixel AI. This may be added to a future release, if I can figure it out
