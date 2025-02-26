#
# Copyright (C) 2011-2021 Entware
#
# This is free software, licensed under the GNU General Public License v2.
# See /LICENSE for more information.
#

include $(TOPDIR)/rules.mk

PKG_NAME:=mpdscribble
PKG_VERSION:=0.23
PKG_REV:=bba2687581cc7f6f62409b8565a9188e7feea205
PKG_RELEASE:=2

PKG_SOURCE:=$(PKG_NAME)-$(PKG_VERSION).tar.bz2
PKG_SOURCE_SUBDIR:=$(PKG_NAME)-$(PKG_VERSION)
PKG_SOURCE_URL:=https://github.com/MusicPlayerDaemon/mpdscribble.git
PKG_SOURCE_PROTO:=git
PKG_SOURCE_VERSION:=$(PKG_REV)
PKG_MIRROR_HASH:=c5656d38bab7ea9dd9cb58af093504186be3345aa4e7d61cb2e5f8fa4ae60425

PKG_BUILD_DEPENDS:=boost

include $(INCLUDE_DIR)/package.mk
include $(INCLUDE_DIR)/meson.mk

define Package/mpdscribble
	SECTION:=sound
	CATEGORY:=Sound
	DEPENDS:=+libgcrypt +libmpdclient +libcurl +libstdcpp
	TITLE:=MPD player with Last.fm scrobbler
	URL:=http://mpd.wikia.com/wiki/Client:Mpdscribble
	MAINTAINER:=Entware team, https://entware.net
endef

define Package/mpdscribble/description
 MPD scribble is a music player daemon client which submits information about
 tracks being played to Last.fm.
endef

MESON_ARGS += \
	-Dsystemd=disabled

MESON_VARS+=BOOST_ROOT=$(STAGING_DIR)/opt

TARGET_CFLAGS += $(shell $(STAGING_DIR)/opt/bin/libgcrypt-config --cflags)
TARGET_LDFLAGS += $(shell $(STAGING_DIR)/opt/bin/libgcrypt-config --libs)

define Package/mpdscribble/install
	$(INSTALL_DIR) $(1)/opt/bin
	$(INSTALL_BIN) $(PKG_INSTALL_DIR)/opt/bin/mpdscribble $(1)/opt/bin
	$(INSTALL_DIR) $(1)/opt/etc
	$(INSTALL_CONF) $(PKG_INSTALL_DIR)/opt/etc/mpdscribble.conf $(1)/opt/etc
endef

define Package/mpdscribble/conffiles
/opt/etc/mpdscribble.conf
endef

$(eval $(call BuildPackage,mpdscribble))
