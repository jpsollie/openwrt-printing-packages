#
# Copyright (C) 2007-2013 OpenWrt.org
#
# This is free software, licensed under the GNU General Public License v2.
# See /LICENSE for more information.
#

include $(TOPDIR)/rules.mk

PKG_NAME:=qpdf
PKG_VERSION:=11.10.1
PKG_RELEASE:=1

PKG_SOURCE:=$(PKG_NAME)-$(PKG_VERSION).tar.gz
PKG_SOURCE_URL:=https://github.com/qpdf/qpdf/releases/download/v$(PKG_VERSION)/$(PKG-SOURCE)
PKG_MD5SUM:=1ff2340ee610bd8d1e1296d3523c79c9

CMAKE_INSTALL:=1

include $(INCLUDE_DIR)/package.mk
include $(INCLUDE_DIR)/cmake.mk

define Package/qpdf
  SECTION:=utils
  CATEGORY:=Utilities
  TITLE:=QPDF is a command-line program for transformations on PDF files.
  DEPENDS:= +libpcre +zlib +libstdcpp +libatomic +libopenssl +libjpeg-turbo
  URL:=http://qpdf.sourceforge.net/
  SUBMENU:=Printing
endef

define Package/qpdf/description
QPDF is a command-line program that does structural, content-preserving
transformations on PDF files. It could have been called something like pdf-to-pdf.
It also provides  many useful capabilities to developers of PDF-producing software
or for people who just want to look at the innards of a PDF file to learn more
about how they work.
endef

CMAKE_OPTIONS += \
	-DBUILD_DOC:BOOL=OFF \
	-DBUILD_SHARED_LIBS:BOOL=ON \
	-DBUILD_STATIC_LIBS:BOOL=OFF \
	-DUSE_IMPLICIT_CRYPTO:BOOL=OFF \
	-DALLOW_CRYPTO_NATIVE:BOOL=OFF \
	-DREQUIRE_CRYPTO_OPENSSL:BOOL=ON

define Package/qpdf/install
	$(INSTALL_DIR) $(1)/usr/bin $(1)/usr/lib
	$(INSTALL_BIN) $(PKG_INSTALL_DIR)/usr/bin/* $(1)/usr/bin/
	$(CP) $(PKG_INSTALL_DIR)/usr/lib/* $(1)/usr/lib/
endef

define Build/InstallDev
	$(INSTALL_DIR) $(1)/usr/bin $(1)/usr/lib
	$(INSTALL_BIN) $(PKG_INSTALL_DIR)/usr/bin/* $(1)/usr/bin/
	$(INSTALL_DIR) $(1)/usr/include
	$(CP) -r $(PKG_INSTALL_DIR)/usr/include/$(PKG_NAME) $(1)/usr/include/
	$(CP) $(PKG_INSTALL_DIR)/usr/lib/* $(1)/usr/lib
endef

$(eval $(call BuildPackage,qpdf))
