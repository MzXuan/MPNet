default_target: all

# get a list of subdirs to build by reading tobuild.txt
SUBDIRS:=$(shell grep -v "^\#" tobuild.txt)

#force to build on the top level build dir
BUILD_PREFIX=`pwd`/build

export PKG_CONFIG_PATH := /home/xuan/Code/MPNet/data_generation/lcmtypes/pod-build/lib/pkgconfig:$(PKG_CONFIG_PATH)
# echo $(PKG_CONFIG_PATH)

# build quietly by default.  For a verbose build, run "make VERBOSE=1"
$(VERBOSE).SILENT:

all: 
	@[ -d $(BUILD_PREFIX) ] || mkdir -p $(BUILD_PREFIX) || exit 1
	@for subdir in $(SUBDIRS); do \
		echo "\n-------------------------------------------"; \
		echo "-- $$subdir"; \
		echo "-------------------------------------------"; \
		$(MAKE) -C $$subdir all || exit 2; \
	done
	@# Place additional commands here if you have any

clean:
	@for subdir in $(SUBDIRS); do \
		echo "\n-------------------------------------------"; \
		echo "-- $$subdir"; \
		echo "-------------------------------------------"; \
		$(MAKE) -C $$subdir clean; \
	done
	rm -rf build/bin
	rm -rf build/include
	rm -rf build/lib
	rm -rf build/share
	@# Place additional commands here if you have any
