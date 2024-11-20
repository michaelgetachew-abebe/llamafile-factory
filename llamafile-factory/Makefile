.PHONY: help build clean install

.DEFAULT_GOAL := help

help:
	@echo "Available targets:"
	@echo "	build		- Build the project"
	@echo "	clean		- Clean the build files"
	@echo "	install		- Install the project"
	@echo " clean-all 	- Remove all generated files including the source files"
	@echo ""
	@echo "** To use a target, run 'make <target>'"

	@echo "Arguments to Customize:"
	@echo "	model_name			- the final name to be used for the llamafile"
	@echo "	download_url		- the HuggingFace model download url"
	@echo "	license_url			- the LICENSE url in the HuggingFace Repository"
	@echo "	llamafile_version"	- the version of the llamafile to use

build:
	@echo "Builing the llamafile"

clean:
	@echo "Cleaning build files and artifacts"

install:
	@echo "Installing the project"

clean-all:
	@echo "Removing all files, including the source files ..."