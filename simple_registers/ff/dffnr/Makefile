# Makefile

# defaults
SIM ?= icarus
DUMP_FSDB = 1
COVERAGE = 0
FPGA_LEVEL = 1
ifeq ($(SIM),vcs)
# VCS Options
SIM_BUILD = ./
SIM_ARGS = 
EXTRA_ARGS = 
EXTRA_ARGS := $(EXTRA_ARGS) -debug_access+all
EXTRA_ARGS := $(EXTRA_ARGS) +incdir+
ifeq ($(FPGA_LEVEL),1)
EXTRA_ARGS := $(EXTRA_ARGS) +incdir+${NETLIST_TYPE}
EXTRA_ARGS := $(EXTRA_ARGS) +incdir+${NETLIST_TYPE}/custom_modules
endif
ifeq ($(DUMP_FSDB),1)
EXTRA_ARGS := $(EXTRA_ARGS) -kdb -lca
endif
ifeq ($(COVERAGE),1)
EXTRA_ARGS := $(EXTRA_ARGS) -cm line+tgl+cond+fsm
endif
endif
TOPLEVEL_LANG ?= verilog

VERILOG_SOURCES += dffnr.v

# TOPLEVEL is the name of the toplevel module in your Verilog or VHDL file
TOPLEVEL = dffnr

# MODULE is the basename of the Python test file
MODULE = test_dffnr

# include cocotb's make rules to take care of the simulator setup
include $(shell cocotb-config --makefiles)/Makefile.sim

