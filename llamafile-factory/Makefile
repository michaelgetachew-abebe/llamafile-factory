.PHONY: help build clean install

.DEFAULT_GOAL := help

model_name = "tinyllama"
download_url = "https://huggingface.co/TheBloke/TinyLlama-1.1B-Chat-v1.0-GGUF/resolve/main/tinyllama-1.1b-chat-v1.0.Q2_K.gguf"
license_url = ""
llamafile_version = "llamafile v0.8.16"

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
	@echo "	download_url-		the HuggingFace model(.gguf) download url"
	@echo "	license_url-		the LICENSE url in the HuggingFace Repository"
	@echo "	llamafile_version"-	the version of the llamafile to use
	@echo ""
	@echo "** To override, some default values run make <target> <Argument_name>=<Argument_value>"
	@echo ""

build:
	@echo "Builing the llamafile"
	build/$(model).llamafile: download_llamafile models/$(model).gguf
	mkdir -p build
	cp llamafile/bin/llamafile build/$(model).llamafile
	echo "-m\n$(model).gguf\n-c\n0\n..." >build/.args
	./llamafile/bin/zipalign -j0 build/$(model).llamafile models/$(model).gguf build/.args $(license)
	chmod a+x build/$(model).llamafile

clean:
	@echo "Cleaning build files and artifacts"

install:
	@echo "Installing the project"

clean-all:
	@echo "Removing all files, including the source files ..."

download_quantized_model:
	mkdir -p model
	cd model && curl -L -O -C $(download_url)

models/$(model).gguf:
	mkdir -p models
	cd models && curl -L -O -C - https://assets.maragu.dev/llm/$(model).gguf

download_llamafile:
	curl -L -O -C - https://github.com/Mozilla-Ocho/llamafile/releases/latest/download/llamafile-$(llamafile_version).zip
	unzip llamafile-$(llamafile_version).zip
	rm -f llamafile-$(llamafile_version).zip
	mv llamafile-$(llamafile_version) llamafile