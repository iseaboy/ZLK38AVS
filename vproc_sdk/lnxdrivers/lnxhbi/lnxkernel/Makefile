include $(ROOTDIR)/Makefile.globals
include $(ROOTDIR)/config.mk

LOCAL_PWD=$(ROOTDIR)/lnxdrivers/lnxhbi/lnxkernel

ccflags-y += -I$(ROOTDIR)/include
ccflags-y += -D$(BUILD_TYPE) 
ccflags-y += -zmuldefs
ccflags-y += -I$(LOCAL_PWD)/inc
ccflags-y += -I$(ROOTDIR)/drivers/hbi/inc

#ldflags-y += -L$(INSTALL_LIB_PATH)
#ldflags-y += -lssl
#ldflags-y += -lhbi
# following needs a better way of doing this 
LIB_PATH := ../../../libs
obj-m := hbi.o
hbi-objs := $(LIB_PATH)/ssl.o $(LIB_PATH)/hbi.o hbi_k.o 


all: help
	make -C $(KSRC) M=$(LOCAL_PWD) 
	make -C $(KSRC) M=$(LOCAL_PWD) modules_install

help:
	@echo "ROOTDIR="$(ROOTDIR)
	@echo "INSTALL_LIB_PATH="$(INSTALL_LIB_PATH)

clean:
	rm -rf   *.o *.ko .*cmd *.mod.c .tmp_versions modules.order Module.symvers *.a ../*.o ../*.mod.* ../.*cmd
