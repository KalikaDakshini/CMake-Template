# CMake Template

Simple template file and script to quickly set up CPP projects.

## Pre-requisites

Place the init folder in `~/.config/cpp_template` and cppgo in `~/.local/bin`

## Usage

`cppgo init <dir_name>` - Initialises the directory

`cppgo lib <dir_name>` - Add a library to the folder

`cppgo delete <dir_name>` - Delete an added library

`cppgo build <build_name>` - Build the project. Debug, Release, or RelwithDeb

`cppgo run <build_name>` - Run the project with the desired build

`cppgo test -d <lib_name> [-R <test_name>]` - Run a test specific to a library
