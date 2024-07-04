#
# Copyright (C) 2018 PRPL Foundation
#
# This is free software, licensed under the GNU General Public License v2.
# See /LICENSE for more information.
#

include $(TOPDIR)/rules.mk

PKG_NAME:=prplmesh
PKG_VERSION:=4.2.2
PKG_RELEASE:=2
PKG_BASE_NAME:=prplmesh

PKG_SOURCE_PROTO:=git
#PKG_SOURCE_URL:=https://github.com/prplfoundation/prplMesh.git
#PKG_SOURCE_URL:=https://gitlab.com/prpl-foundation/prplmesh/prplMesh.git
#PKG_SOURCE_URL:=https://gitlab.com/prpl-foundation/prplmesh/prplMesh.git
#PKG_SOURCE_URL:=file:///home/ubuntu/prplMesh/

#PKG_SOURCE_URL:=/home/ubuntu/prplMesh/.git
#PKG_SOURCE_VERSION:=44ba9c5f5f644a6dba226c3738390c356745f042

#PKG_SOURCE_URL:=/home/ubuntu/prplMesh.leonid/.git
#PKG_SOURCE_VERSION:=d7f8039a666423fcda3cb690d8c7d1e0668b852c
PKG_SOURCE_URL:=git@gitlab.com:leonidbobovich/prplMesh.git
PKG_SOURCE_VERSION:=9527573c40de7e897743ad1ab93b36eda05de081

#PKG_SOURCE_DATE:=2024-02-21
#PKG_SOURCE_VERSION:=
#PKG_MIRROR_HASH:=
#PKG_SOURCE_VERSION:=56f2c3531066e461be8911b488b54193fb6b88e0
#PKG_SOURCE_VERSION:=a1a22f8ee37d45218fdd4e8d4112e114b6529f31
#PKG_SOURCE_VERSION:=497d9fbf202880009fb22b8c1475f4868d9a2198
#PKG_MIRROR_HASH:=d200bf556842b0c91da53ec3a514f8c80c39e7e9b6b7f8c72bbef0275252c233

PKG_LICENSE:=BSD-2-Clause-Patent
PKG_LICENSE_FILES:=LICENSE

include $(INCLUDE_DIR)/package.mk
include $(INCLUDE_DIR)/cmake.mk

#CMAKE_OPTIONS += -DBEEROCKS_OPENWRT -DOPENWRT=TRUE -DCMAKE_C_FLAGS='-Wno-deprecated -Wno-deprecated-copy' -DCMAKE_CXX_FLAGS='-Wno-deprecated -Wno-deprecated-copy'
CMAKE_OPTIONS += -DBEEROCKS_OPENWRT=1 -DCMAKE_C_FLAGS='-Wno-deprecated -Wno-deprecated-copy' -DCMAKE_CXX_FLAGS='-Wno-deprecated -Wno-deprecated-copy'

define Package/prplmesh
  SECTION:=net
  CATEGORY:=Network
  TITLE:=An implementation of the Wi-Fi Alliance Multi-AP Specification
  URL:=https://gitlab.com/prpl-foundation/prplmesh/prplMesh.git
  MAINTAINER:=Arnout Vandecappelle (Essensium/Mind) <arnout@mind.be>
  DEPENDS:=+ebtables +libnl-core +libnl-genl +libopenssl +libpthread +librt +libubox +libubus +rpcd +rpcd-mod-iwinfo +libstdcpp +libnl +libnl-route +libnl-core@!BIG_ENDIAN
endef

define Package/prplmesh/description
 The IEEE 1905.1 protocol is a mechanism for home devices to discover each
 other and communicate, so that they can use optimal paths for transmission.
 This package implements the IEEE 1905.1 and 1905.1a protocol, as well as the
 WFA Multi-AP protocol.
endef


define Package/prplmesh/install
	$(INSTALL_DIR)  $(1)/usr/sbin/
	$(INSTALL_BIN)  $(PKG_BUILD_DIR)/out/bin/* $(1)/usr/sbin/
	$(INSTALL_DIR)  $(1)/usr/lib/
	$(INSTALL_BIN)  $(PKG_BUILD_DIR)/out/lib/* $(1)/usr/lib/
	$(INSTALL_DIR) $(1)/etc/config/
	$(INSTALL_DATA) ./files/prplmesh.config $(1)/etc/config/prplmesh
	$(INSTALL_DATA) $(PKG_BUILD_DIR)/out/config/* $(1)/etc/config/
	$(INSTALL_DIR) $(1)/etc/init.d/
	$(INSTALL_BIN) ./files/prplmesh.init $(1)/etc/init.d/prplmesh
endef

$(eval $(call BuildPackage,prplmesh))
