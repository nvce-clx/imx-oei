# Memory size: 2GB or 4GB (default 2GB). Lowercase "mem=" also works.
ifdef mem
    MEM_SIZE := $(mem)
endif
MEM_SIZE ?= 2GB

ifeq ($(filter $(MEM_SIZE),2GB 4GB),)
    $(error MEM_SIZE must be 2GB or 4GB, got '$(MEM_SIZE)')
endif

# DDR speed: 2880 or 4266 MT/s (default 4266). Lowercase "speed=" also works.
ifdef speed
    DDR_SPEED := $(speed)
endif
DDR_SPEED ?= 4266

ifeq ($(filter $(DDR_SPEED),2880 4266),)
    $(error DDR_SPEED must be 2880 or 4266, got '$(DDR_SPEED)')
endif

# Timing file per memory size (file name without .c)
DDR_CONFIG_2GB_2880  = MIMX95_LPDDR4X_CALIXTO_OPTIMA_2GB-2880MTS-TIMING
DDR_CONFIG_2GB_4266  = MIMX95_LPDDR4X_CALIXTO_OPTIMA_2GB-4266MTS-TIMING
DDR_CONFIG_4GB_2880  = MIMX95_LPDDR4X_CALIXTO_OPTIMA_4GB-2880MTS-TIMING
DDR_CONFIG_4GB_4266  = MIMX95_LPDDR4X_CALIXTO_OPTIMA_4GB-4266MTS-TIMING



# DDR_CONFIG on the command line still overrides this
DDR_CONFIG ?= $(DDR_CONFIG_$(MEM_SIZE)_$(DDR_SPEED))

# Catch missing mapping early
ifeq ($(strip $(DDR_CONFIG)),)
    $(error No timing file for $(MEM_SIZE) @ $(DDR_SPEED) MT/s)
endif

OBJS  += $(OUT)/$(DDR_CONFIG).o

VPATH += boards/mx95lp4x-optima/ddr
