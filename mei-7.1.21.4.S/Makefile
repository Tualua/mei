#
# Intel Management Engine Interface (Intel MEI) Linux driver
# Copyright (c) 2010-2011, Intel Corporation.
#
# This program is free software; you can redistribute it and/or modify it
# under the terms and conditions of the GNU General Public License,
# version 2, as published by the Free Software Foundation.
#
# This program is distributed in the hope it will be useful, but WITHOUT
# ANY WARRANTY; without even the implied warranty of MERCHANTABILITY or
# FITNESS FOR A PARTICULAR PURPOSE.  See the GNU General Public License for
# more details.
#
TARGET		:=mei
KVER		:=`uname -r`
KERNELDIR 	:=/lib/modules/$(KVER)
INSTDIR 	:=/kernel/drivers/misc/mei
MODULE_PATH	:=$(KERNELDIR)/$(INSTDIR)/$(TARGET).ko

ifneq ($(KERNELRELEASE),)
include Kbuild
else

EXTRA_CFLAGS += -O2 -Wall

all:
	$(MAKE) -C $(KERNELDIR)/build M=`pwd` modules

clean:
	$(MAKE) -C $(KERNELDIR)/build M=`pwd` clean

install: all
	$(MAKE) INSTALL_MOD_DIR=$(INSTALL_MOD_PATH)$(INSTDIR) -C $(KERNELDIR)/build M=`pwd` modules_install
	/sbin/depmod -a || true


uninstall:
	@echo Uninstalling $(TARGET).ko
	@if [ -e $(INSTALL_MOD_PATH)$(MODULE_PATH) ]; then \
		rm -f $(INSTALL_MOD_PATH)$(MODULE_PATH) ; \
		/sbin/depmod -a || true; \
	else \
		echo $(TARGET).ko is not installed; \
	fi

.PHONY: all clean install uninstall

endif