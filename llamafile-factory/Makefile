.PHONY: help build clean install

.DEFAULT_GOAL := help

model_name :=tinyllama
download_url :=https://huggingface.co/TheBloke/TinyLlama-1.1B-Chat-v1.0-GGUF/resolve/main/tinyllama-1.1b-chat-v1.0.Q2_K.gguf
license_url :=LICENSE
llamafile_version :=0.8.16

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

build: download_llamafile download_quantized_model
	@echo "Builing the llamafile"
	mkdir -p build
	cp llamafile/bin/llamafile build/$(model_name).llamafile
	echo "-m\n$(model_name).gguf\n-c\n0\n..." >build/.args
	./llamafile/bin/zipalign -j0 build/$(model_name).llamafile model/tinyllama-1.1b-chat-v1.0.Q2_K.gguf build/.args $(license)
	chmod a+x build/$(model_name).llamafile

clean:
	@echo "Cleaning build files and artifacts"

install:
	@echo "Installing the project"

clean-all:
	@echo "Removing all files, including the source files ..."

download_quantized_model:
	mkdir -p model
	cd model && curl -L -O $(download_url) -o $(model_name).gguf

download_llamafile:
	curl -L -O -C - https://github.com/Mozilla-Ocho/llamafile/releases/download/0.8.16/llamafile-$(llamafile_version).zip
	unzip llamafile-$(llamafile_version).zip
	rm -f llamafile-$(llamafile_version).zip
	mv llamafile-$(llamafile_version) llamafile