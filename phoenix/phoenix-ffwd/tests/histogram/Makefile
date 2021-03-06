#------------------------------------------------------------------------------
# Copyright (c) 2007-2009, Stanford University
# All rights reserved.
#
# Redistribution and use in source and binary forms, with or without
# modification, are permitted provided that the following conditions are met:
#     * Redistributions of source code must retain the above copyright
#       notice, this list of conditions and the following disclaimer.
#     * Redistributions in binary form must reproduce the above copyright
#       notice, this list of conditions and the following disclaimer in the
#       documentation and/or other materials provided with the distribution.
#     * Neither the name of Stanford University nor the names of its 
#       contributors may be used to endorse or promote products derived from 
#       this software without specific prior written permission.
#
# THIS SOFTWARE IS PROVIDED BY STANFORD UNIVERSITY ``AS IS'' AND ANY
# EXPRESS OR IMPLIED WARRANTIES, INCLUDING, BUT NOT LIMITED TO, THE IMPLIED
# WARRANTIES OF MERCHANTABILITY AND FITNESS FOR A PARTICULAR PURPOSE ARE
# DISCLAIMED. IN NO EVENT SHALL STANFORD UNIVERSITY BE LIABLE FOR ANY
# DIRECT, INDIRECT, INCIDENTAL, SPECIAL, EXEMPLARY, OR CONSEQUENTIAL DAMAGES
# (INCLUDING, BUT NOT LIMITED TO, PROCUREMENT OF SUBSTITUTE GOODS OR SERVICES;
# LOSS OF USE, DATA, OR PROFITS; OR BUSINESS INTERRUPTION) HOWEVER CAUSED AND
# ON ANY THEORY OF LIABILITY, WHETHER IN CONTRACT, STRICT LIABILITY, OR TORT
# (INCLUDING NEGLIGENCE OR OTHERWISE) ARISING IN ANY WAY OUT OF THE USE OF THIS
# SOFTWARE, EVEN IF ADVISED OF THE POSSIBILITY OF SUCH DAMAGE.
#------------------------------------------------------------------------------ 

# This Makefile requires GNU make.

HOME = ../..

include $(HOME)/Defines.mk

LIBS_RCL = -lpthread -L$(HOME)/$(LIB_DIR) -l$(PHOENIX_RCL) $(LIBLOCK) -lpapi
LIBS += -L$(HOME)/$(LIB_DIR) -l$(PHOENIX)

HIST_OBJS = histogram.o
HIST_SEQ_OBJS = histogram-seq.o
HIST_PTHREAD_OBJS = histogram-pthread.o
HIST_RCL_OBJS = histogram-rcl.o
HIST_PTHREAD_RCL_OBJS = histogram-pthread-rcl.o

PROGS = histogram-rcl histogram-pthread-rcl histogram histogram-seq histogram-pthread

.PHONY: default all clean

default: all

all: $(PROGS)

histogram: $(HIST_OBJS) $(LIB_DEP)
	$(CC) $(CFLAGS) -o $@ $(HIST_OBJS) $(LIBS)

histogram-seq: $(HIST_SEQ_OBJS)
	$(CC) $(CFLAGS) -o $@ $(HIST_SEQ_OBJS) $(LIBS)

histogram-pthread: $(HIST_PTHREAD_OBJS)
	$(CC) $(CFLAGS) -o $@ $(HIST_PTHREAD_OBJS) $(LIBS)

histogram-rcl: $(HIST_RCL_OBJS) $(LIB_RCL_DEP)
	$(CC) $(CFLAGS) -o $@  $(HIST_RCL_OBJS) $(LIBS_RCL)

histogram-pthread-rcl: $(HIST_PTHREAD_RCL_OBJS) $(LIB_RCL_DEP)
	$(CC) $(CFLAGS) -o $@ $(HIST_PTHREAD_RCL_OBJS) $(LIBS_RCL)

%.o: %.c
	$(CC) $(CFLAGS) -c $< -o $@ -I$(HOME)/$(INC_DIR)

clean:
	rm -f $(PROGS) $(HIST_OBJS) $(HIST_SEQ_OBJS) $(HIST_PTHREAD_OBJS) $(HIST_RCL_OBJS) $(HIST_PTHREAD_RCL_OBJS)
