#
# Copyright (C) 2006-2016 OpenWrt.org
#
# This is free software, licensed under the GNU General Public License v2.
# See /LICENSE for more information.
#
include $(TOPDIR)/rules.mk

PKG_NAME:=cmake
PKG_VERSION:=3.25.2
PKG_RELEASE:=1
PKG_CPE_ID:=cpe:/a:kitware:cmake

PKG_SOURCE:=$(PKG_NAME)-$(PKG_VERSION).tar.gz
PKG_SOURCE_URL:=https://github.com/Kitware/CMake/releases/download/v$(PKG_VERSION)/ \
		https://cmake.org/files/v3.25/
PKG_HASH:=c026f22cb931dd532f648f087d587f07a1843c6e66a3dfca4fb0ea21944ed33c


HOST_BUILD_PARALLEL:=1
HOST_CONFIGURE_PARALLEL:=1

include $(INCLUDE_DIR)/host-build.mk

HOST_CONFIGURE_VARS += \
	CC="$(HOSTCC_NOCACHE)" \
	CXX="$(HOSTCXX_NOCACHE)" \
	MAKEFLAGS="$(HOST_JOBS)" \
	CXXFLAGS="$(HOST_CFLAGS)"

HOST_CONFIGURE_ARGS := \
	$(if $(MAKE_JOBSERVER),--parallel="$(MAKE_JOBSERVER)") \
	--prefix=$(STAGING_DIR_HOST)

ifneq ($(findstring c,$(OPENWRT_VERBOSE)),)
  HOST_MAKE_FLAGS += VERBOSE=1
endif

$(eval $(call HostBuild))