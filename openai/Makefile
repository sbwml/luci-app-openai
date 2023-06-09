#
# Copyright (C) 2015-2016 OpenWrt.org
#
# This is free software, licensed under the GNU General Public License v3.
#

include $(TOPDIR)/rules.mk

PKG_NAME:=openai
PKG_VERSION:=20230609
PKG_RELEASE:=1
STRIP:=false

PKG_SOURCE_URL:=https://us.cooluc.com/openai/
PKG_SOURCE:=openai-$(PKG_VERSION)-linux-musl-$(ARCH).tar.gz

# Binary by next.js server + nodejs16
ifeq ($(ARCH),aarch64)
  PKG_HASH:=8f6ee07e5042e554b197ded7af09df1327f5ecc38297260797720c839cb7771e
else ifeq ($(ARCH),x86_64)
  PKG_HASH:=fc2a9c1934ede97999fe412db78beb1215fa6d0d880550d3622343c8c2c26c04
endif

PKG_MAINTAINER:=sbwml <admin@cooluc.com>
PKG_BUILD_DIR:=$(BUILD_DIR)/$(PKG_NAME)-$(PKG_VERSION)
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