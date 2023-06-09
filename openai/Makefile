#
# Copyright (C) 2015-2016 OpenWrt.org
#
# This is free software, licensed under the GNU General Public License v3.
#

include $(TOPDIR)/rules.mk

PKG_NAME:=openai
PKG_VERSION:=2.7-24bf15a
PKG_RELEASE:=1
STRIP:=false

PKG_SOURCE_URL:=https://github.com/sbwml/chatgpt-next/releases/download/v$(PKG_VERSION)/
PKG_SOURCE:=openai-v$(PKG_VERSION)-linux-musl-$(ARCH).tar.gz

# Binary by next.js server + nodejs16
ifeq ($(ARCH),aarch64)
  PKG_HASH:=aecd0e7a5a1375ee7bce1a2303cf1ec569f9681ceb99634049d6101d8cc23bb8
else ifeq ($(ARCH),x86_64)
  PKG_HASH:=e28053aa3b2826af99b496a8b8f92915519518a586568dd71d3fc3d3e916af32
endif

PKG_MAINTAINER:=sbwml <admin@cooluc.com>
PKG_BUILD_DIR:=$(BUILD_DIR)/$(PKG_NAME)-v$(PKG_VERSION)-linux-musl-$(ARCH)
include $(INCLUDE_DIR)/package.mk

define Package/$(PKG_NAME)
  SECTION:=net
  CATEGORY:=Network
  SUBMENU:=Web Servers/Proxies
  TITLE:=ChatGPT WebUI
  URL:=https://github.com/Yidadaa/ChatGPT-Next-Web
  DEPENDS:=@(aarch64||x86_64) @USE_MUSL
endef

define Package/$(PKG_NAME)/description
  ChatGPT Web UI on Vercel.
endef

define Package/$(PKG_NAME)/postrm
#!/bin/sh
rm -rf /snapshot
exit 0
endef

define Build/Compile
endef

define Package/$(PKG_NAME)/install
	$(INSTALL_DIR) $(1)/usr/bin
	$(INSTALL_BIN) $(PKG_BUILD_DIR)/openai $(1)/usr/bin/openai

	$(INSTALL_DIR) $(1)/etc/config
	$(INSTALL_CONF) $(CURDIR)/files/openai.config $(1)/etc/config/openai
	$(INSTALL_DIR) $(1)/etc/init.d
	$(INSTALL_BIN) $(CURDIR)/files/openai.init $(1)/etc/init.d/openai
	$(INSTALL_DIR) $(1)/snapshot/sbwml
	$(INSTALL_DATA) $(CURDIR)/files/authenticate.md $(1)/snapshot/sbwml/
endef

$(eval $(call BuildPackage,$(PKG_NAME)))
