#
# Copyright (C) 2015-2017 OpenWrt.org
#
# This is free software, licensed under the GNU General Public License v2.
# See /LICENSE for more information.
#

include $(TOPDIR)/rules.mk

PKG_NAME:=python-egenix-mx-base
PKG_VERSION:=3.2.9
PKG_RELEASE:=1
PKG_MAINTAINER:=Dmitry Trefilov <the-alien@live.ru>
PKG_LICENSE:=eGenix.com Public License 1.1.0
PKG_LICENSE_FILES:=LICENSE COPYRIGHT

PKG_SOURCE:=egenix-mx-base-$(PKG_VERSION).tar.gz
PKG_SOURCE_URL:=https://downloads.egenix.com/python/
PKG_MD5SUM:=b6f6612a95a857659e20968f496dfcc2

PKG_BUILD_DIR:=$(BUILD_DIR)/egenix-mx-base-$(PKG_VERSION)
PKG_BUILD_DEPENDS:=python

include $(INCLUDE_DIR)/package.mk
$(call include_mk, python-package.mk)
$(call include_mk, python3-package.mk)

PKG_UNPACK:=$(HOST_TAR) -C $(PKG_BUILD_DIR) --strip-components=1 -xzf $(DL_DIR)/$(PKG_SOURCE)

define Package/python-egenix-mx-base/Default
  SUBMENU:=Python
  SECTION:=lang
  CATEGORY:=Languages
  DEPENDS:=+USE_EGLIBC:librt +USE_UCLIBC:librt
  URL:=http://www.egenix.com/products/python/mxBase/
endef

define Package/python-egenix-mx-base
  $(call Package/python-egenix-mx-base/Default)
  TITLE:=Python Egenix mxBase
  DEPENDS:=PACKAGE_python-egenix-mx-base:python
endef

define Package/python3-egenix-mx-base
  $(call Package/python-egenix-mx-base/Default)
  TITLE:=Python3 Egenix mxBase
  DEPENDS:=PACKAGE_python-egenix-mx-base:python3
endef

define Package/python-egenix-mx-base/description
 The eGenix.com mx Base Distribution for Python is a collection
 of professional quality software tools which enhance Python's
 usability in many important areas such as fast text searching,
 date/time processing and high speed data types.
endef

define Package/python3-egenix-mx-base/description
$(call Package/python-egenix-mx-base/description)
.
(Variant for Python3)
endef

$(eval $(call PyPackage,python-egenix-mx-base))
$(eval $(call BuildPackage,python-egenix-mx-base))
$(eval $(call Py3Package,python3-egenix-mx-base))
$(eval $(call Build3Package,python3-egenix-mx-base))
