rebuild?=0

default: all
.PHONY: default

clean:
	rm -rf build
.PHONY: clean

conan_install:
	conan install . --output-folder=build --build=missing
.PHONY: conan_install

generate:
	cmake --preset conan-release
.PHONY: generate

build:
	cmake --build --preset conan-release
.PHONY: build

run:
	./build/compressor
.PHONY: run

all: clean conan_install generate build run
.PHONY: all