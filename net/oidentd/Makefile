#
# Copyright (C) 2006-2011 OpenWrt.org
#
# This is free software, licensed under the GNU General Public License v2.
# See /LICENSE for more information.
#

include $(TOPDIR)/rules.mk

PKG_NAME:=oidentd
PKG_VERSION:=2.0.9
PKG_RELEASE:=1

PKG_BUILD_DIR:=$(BUILD_DIR)/oidentd-$(PKG_VERSION)

PKG_SOURCE_PROTO:=git
PKG_SOURCE_URL:=git://github.com/ryan-mccabe/oidentd.git
PKG_SOURCE_VERSION:=1727f6f0a5f55ff41e2b681f17a2b1815abd0863
PKG_SOURCE:=$(PKG_NAME)-$(PKG_SOURCE_VERSION).tar.gz
PKG_CAT:=zcat

PKG_FIXUP:=autoreconf

include $(INCLUDE_DIR)/package.mk

define Package/oidentd
  SECTION:=base
  CATEGORY:=Network
  TITLE:=Identd server
  URL:=http://dev.ojnk.net/
endef

define Package/oidentd/description
	A nat aware identd server that will correctly forwared requests to clients.
endef

# uses GNU configure

define Build/Configure
	$(call Build/Configure/Default)
endef

define Package/oidentd/install
	$(INSTALL_DIR) $(1)/usr/sbin
	$(CP) $(PKG_BUILD_DIR)/src/oidentd $(1)/usr/sbin/
	$(INSTALL_DIR) $(1)/etc/init.d
	$(INSTALL_BIN) ./files/oidentd.init $(1)/etc/init.d/oidentd
endef

$(eval $(call BuildPackage,oidentd))
