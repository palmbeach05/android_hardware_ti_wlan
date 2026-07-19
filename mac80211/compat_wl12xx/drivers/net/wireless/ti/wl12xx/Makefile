wl12xx-objs	= main.o

define filechk_version.h
	(echo 'static const char *wl12xx_timestamp = __TIMESTAMP__;'; \
	echo 'static const char *wl12xx_git_head = \
			"$(shell git describe --dirty)";')
endef

$(obj)/version.h: .git/HEAD .git/index .git/refs/tags
	@$(call filechk,version.h)

$(obj)/main.c: $(src)/version.h

# convert all wl12xx-objs to $(src)/file form
define WL12XX_OBJS_SRC
$(shell echo $(wl12xx-objs) |
	awk '{for (i=1;i<=NF;i++) {printf "$(src)/%s ", $$i} }')
endef

obj-$(CONFIG_WL12XX)		+= wl12xx.o
