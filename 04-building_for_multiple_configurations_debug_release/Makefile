SHELL=/bin/bash

rebuild?=0
buildtype?=release

default: all
.PHONY: default

clean:
	rm -rf build
.PHONY: clean

conan_install:
	conan install . --output-folder=build --build=missing --profile ./.conan/profiles/$(buildtype)
.PHONY: conan_install

generate:
	source ./build/conanbuild.sh && \
	cmake --version ; \
	source ./build/deactivate_conanbuild.sh

	source ./build/conanbuild.sh && \
	cmake --preset conan-$(buildtype) ; \
	source ./build/deactivate_conanbuild.sh
.PHONY: generate

build:
	source ./build/conanbuild.sh && \
	cmake --build --preset conan-$(buildtype) ; \
	source ./build/deactivate_conanbuild.sh
.PHONY: build

run:
	./build/compressor
.PHONY: run

all: clean conan_install generate build run
.PHONY: all