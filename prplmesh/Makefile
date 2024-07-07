#
# Copyright (C) 2018 PRPL Foundation
#
# This is free software, licensed under the GNU General Public License v2.
# See /LICENSE for more information.
#

include $(TOPDIR)/rules.mk

PKG_NAME:=prplmesh
PKG_VERSION:=4.2.4
PKG_RELEASE:=0
PKG_BASE_NAME:=prplmesh

PKG_SOURCE_PROTO:=git
PKG_SOURCE_URL:=git@gitlab.com:leonidbobovich/prplMesh.git
#PKG_SOURCE_VERSION:=d7f8039a666423fcda3cb690d8c7d1e0668b852c
PKG_SOURCE_VERSION:=HEAD
#PKG_SOURCE_DATE:=2024-02-21
#PKG_MIRROR_HASH:=d200bf556842b0c91da53ec3a514f8c80c39e7e9b6b7f8c72bbef0275252c233

PKG_LICENSE:=BSD-2-Clause-Patent
PKG_LICENSE_FILES:=LICENSE

include $(INCLUDE_DIR)/package.mk
include $(INCLUDE_DIR)/cmake.mk

#CMAKE_OPTIONS += -DBEEROCKS_OPENWRT -DOPENWRT=TRUE -DCMAKE_C_FLAGS='-Wno-deprecated -Wno-deprecated-copy' -DCMAKE_CXX_FLAGS='-Wno-deprecated -Wno-deprecated-copy'
#CMAKE_OPTIONS += -DCMAKE_INSTALL_MODE=REL_SYMLINK -DBEEROCKS_OPENWRT=1 -DCMAKE_C_FLAGS='-Wno-deprecated -Wno-deprecated-copy -Wno-psabi' -DCMAKE_CXX_FLAGS='-Wno-deprecated -Wno-deprecated-copy -Wno-psabi'
CMAKE_OPTIONS += -DCMAKE_INSTALL_MODE=REL_SYMLINK -DCMAKE_C_FLAGS='-Wall' -DCMAKE_CXX_FLAGS='-Wall'

define Package/prplmesh
  SECTION:=net
  CATEGORY:=Network
  TITLE:=An implementation of the Wi-Fi Alliance Multi-AP Specification
  URL:=https://github.com/leonidbobovich/prplMesh-openwrt.git
  MAINTAINER:= Leonid Bobovich <leonidbobovich@gmail.com>
  DEPENDS:=+ebtables +libnl-core +libnl-genl +libopenssl +libpthread +librt +libubox +libubus +rpcd +rpcd-mod-iwinfo +libstdcpp +libnl +libnl-route
endef

define Package/prplmesh/description
 The IEEE 1905.1 protocol is a mechanism for home devices to discover each
 other and communicate, so that they can use optimal paths for transmission.
 This package implements the IEEE 1905.1 and 1905.1a protocol, as well as the
 WFA Multi-AP protocol.
endef


#	$(INSTALL_DIR)  $(1)/usr/bin
#	$(INSTALL_LIB)  $(PKG_BUILD_DIR)/out/lib $(1)/usr/lib
#
define Package/prplmesh/install
	$(INSTALL_DIR)  $(1)/usr
	$(CP)  $(PKG_BUILD_DIR)/out $(1)/usr
	$(INSTALL_DIR)  $(1)/etc/config/
	$(INSTALL_DATA) ./files/prplmesh.config $(1)/etc/config/prplmesh
	$(INSTALL_DIR)  $(1)/etc/init.d/
	$(INSTALL_BIN)  ./files/prplmesh.init $(1)/etc/init.d/prplmesh
endef

$(eval $(call BuildPackage,prplmesh))
