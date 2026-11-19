# Memory size: 2GB or 4GB (default 2GB). Lowercase "mem=" also works.
ifdef mem
    MEM_SIZE := $(mem)
endif
MEM_SIZE ?= 2GB

# Timing file per memory size (file name without .c)
DDR_CONFIG_2GB = MIMX95_LPDDR4X_CALIXTO_OPTIMA_4266MTS_2GB_timing
DDR_CONFIG_4GB = MIMX95_LPDDR4X_CALIXTO_OPTIMA_2880MTS_4GB_timing

ifeq ($(filter $(MEM_SIZE),2GB 4GB),)
    $(error MEM_SIZE must be 2GB or 4GB, got '$(MEM_SIZE)')
endif

# DDR_CONFIG on the command line still overrides this
DDR_CONFIG ?= $(DDR_CONFIG_$(MEM_SIZE))
OBJS  += $(OUT)/$(DDR_CONFIG).o

VPATH += boards/mx95lp4x-optima/ddr
