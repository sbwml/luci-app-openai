#
# Copyright (C) 2015-2016 OpenWrt.org
#
# This is free software, licensed under the GNU General Public License v3.
#

include $(TOPDIR)/rules.mk

PKG_NAME:=openai
PKG_VERSION:=2.8.6-0ec4cc2
PKG_RELEASE:=2
STRIP:=false

PKG_SOURCE_URL:=https://github.com/sbwml/chatgpt-next/releases/download/v$(PKG_VERSION)/
PKG_SOURCE:=openai-v$(PKG_VERSION)-linux-musl-$(ARCH).tar.gz

ifeq ($(ARCH),aarch64)
  PKG_HASH:=3cccc5a37408f12be994cefa32d2d49e343a827966012deb4418f71818d527d7
else ifeq ($(ARCH),x86_64)
  PKG_HASH:=87e1f5da6c0a4116e75dcdbc4bc9f3ec59884f458101c97beb5e5a56da8d6064
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
  Next.js based ChatGPT Web UI.
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
endef

$(eval $(call BuildPackage,$(PKG_NAME)))
