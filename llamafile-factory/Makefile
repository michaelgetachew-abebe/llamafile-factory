.PHONY: help build clean install

.DEFAULT_GOAL := help

model_name = ""
download_url = ""
license_url = ""
llamafile_version = ""

help:
	@echo ""
	@echo "Available targets:"

	@echo "	build-		Build the project"
	@echo "	clean-		Clean the build files"
	@echo "	install-	Install the project"
	@echo ""
	@echo "** To use a target, run 'make <target>'"

	@echo "Arguments to Customize:"

	@echo "	model_name-			the final name to be used for the llamafile"
	@echo "	download_url-		the HuggingFace model download url"
	@echo "	license_url-		the LICENSE url in the HuggingFace Repository"
	@echo "	llamafile_version"-	the version of the llamafile to use
	@echo ""
	@echo "** To override, some default values run make <target> <Argument_name>=<Argument_value>"
	@echo ""

build:
	@echo "Builing the llamafile"

clean:
	@echo "Cleaning build files and artifacts"

install:
	@echo "Installing the project"

clean-all:
	@echo "Removing all files, including the source files ..."