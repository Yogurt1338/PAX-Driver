KERNEL_VER := $(shell uname -r)
KERNEL_DIR := /lib/modules/$(KERNEL_VER)/build
INSTALL_DIR := /lib/modules/$(KERNEL_VER)/ttyPos

# Add debug flags and warnings, but suppress unused parameter warnings
ccflags-y += -Wall -Wextra -g -Wno-unused-parameter
obj-m := ttyPos.o

# Simplified dkms target
dkms:
	$(MAKE) -C $(KERNEL_DIR) M=$(PWD) modules

# Main build target
all:
	$(MAKE) -C $(KERNEL_DIR) M=$(PWD) modules

# Clean target with more thorough cleanup
clean:
	$(MAKE) -C $(KERNEL_DIR) M=$(PWD) clean
	rm -f Module.symvers Module.markers modules.order
	rm -rf .tmp_versions

# Installation target
install: all
	@mkdir -p $(INSTALL_DIR)
	install -m 644 ttyPos.ko $(INSTALL_DIR)/ttyPos.ko
	/sbin/depmod -a

# Uninstallation target
uninstall:
	-/sbin/modprobe -r ttyPos
	rm -f $(INSTALL_DIR)/ttyPos.ko
	/sbin/depmod -a

# Declare phony targets
.PHONY: all clean install uninstall dkms
