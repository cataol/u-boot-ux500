#
# Copyright (C) ST-Ericsson SA 2009
#
# See file CREDITS for list of people who contributed to this
# project.
#
# This program is free software; you can redistribute it and/or
# modify it under the terms of the GNU General Public License as
# published by the Free Software Foundation; either version 2 of
# the License, or (at your option) any later version.
#
# This program is distributed in the hope that it will be useful,
# but WITHOUT ANY WARRANTY; without even the implied warranty of
# MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
# GNU General Public License for more details.
#
# You should have received a copy of the GNU General Public License
# along with this program; if not, write to the Free Software
# Foundation, Inc., 59 Temple Place, Suite 330, Boston,
# MA 02111-1307 USA
#


include $(TOPDIR)/config.mk

LIB	= $(obj)lib$(BOARD).a

COBJS	:= u8500.o u8500_i2c.o mmc_host.o mmc_utils.o ab8500vibra.o cmd_cdump.o
SOBJS	:= mmc_fifo.o

COBJS-$(CONFIG_VIDEO_LOGO) += mcde_display.o mcde_display_dsi.o mcde_display_dpi.o
COBJS-$(CONFIG_VIDEO_LOGO) += mcde_hw.o mcde_display_image.o

COBJS	+= $(COBJS-y)

SRCS	:= $(SOBJS:.o=.S) $(COBJS:.o=.c)
OBJS	:= $(addprefix $(obj),$(COBJS))
SOBJS	:= $(addprefix $(obj),$(SOBJS))

$(obj)mmc_host.o: CFLAGS += -O2

$(LIB): $(obj).depend $(OBJS) $(SOBJS)
	$(AR) $(ARFLAGS) $@ $(OBJS) $(SOBJS)

clean:
	rm -f $(SOBJS) $(OBJS)

distclean:	clean
	rm -f $(LIB) core *.bak $(obj).depend

#########################################################################

# defines $(obj).depend target
include $(SRCTREE)/rules.mk

sinclude $(obj).depend

#########################################################################
