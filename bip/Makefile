#
# Copyright (C) 2011-2021 Entware
#
# This is free software, licensed under the GNU General Public License v2.
# See /LICENSE for more information.
#

include $(TOPDIR)/rules.mk

PKG_NAME:=bip
PKG_VERSION:=0.9.2
PKG_RELEASE:=1

PKG_SOURCE:=$(PKG_NAME)-$(PKG_VERSION).tar.gz
PKG_SOURCE_URL:=https://projects.duckcorp.org/attachments/download/103
PKG_HASH:=f643b39b7af2a0d5fe7c45c57ffe3e6710be33278455eab8aeefe5b2842764ea

PKG_INSTALL:=1

include $(INCLUDE_DIR)/package.mk

define Package/bip
	SECTION:=net
	CATEGORY:=Network
	SUBMENU:=Instant Messaging
	DEPENDS:=+libopenssl
	TITLE:=multi user irc proxy
	URL:=https://projects.duckcorp.org/projects/bip
	MAINTAINER:=Entware team, https://entware.net
endef

define Package/bip/description
 Bip is an IRC proxy, which means it keeps connected to your preferred
 IRC servers, can store the logs for you, and even send them back to your
 IRC client(s) upon connection.
endef

define Package/bip/conffiles
/opt/etc/bip.conf
endef

define Package/bip/install
	$(INSTALL_DIR) $(1)/opt/bin
	$(INSTALL_BIN) $(PKG_INSTALL_DIR)/opt/bin/bip{,mkpw} $(1)/opt/bin
	$(INSTALL_DIR) $(1)/opt/etc/init.d
	$(INSTALL_CONF) \
		$(PKG_INSTALL_DIR)/opt/share/doc/bip/examples/bip.conf \
		$(1)/opt/etc
	$(INSTALL_BIN) ./files/S99bip $(1)/opt/etc/init.d
endef

$(eval $(call BuildPackage,bip))
