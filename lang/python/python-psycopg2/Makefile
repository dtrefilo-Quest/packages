#
# Copyright (C) 2015-2017 OpenWrt.org
#
# This is free software, licensed under the GNU General Public License v2.
# See /LICENSE for more information.
#

include $(TOPDIR)/rules.mk

PKG_NAME:=python-psycopg2
PKG_VERSION:=2.7.3
PKG_RELEASE:=1
PKG_MAINTAINER:=Dmitry Trefilov <the-alien@live.ru>
PKG_LICENSE:=LGPL-3.0+
PKG_LICENSE_FILES:=LICENSE

PKG_SOURCE:=psycopg2-$(PKG_VERSION).tar.gz
PKG_SOURCE_URL:=http://initd.org/psycopg/tarballs/PSYCOPG-2-7/
PKG_MD5SUM:=f9823ffedcec57a8c036e67c6fb3fa36

PKG_BUILD_DIR:=$(BUILD_DIR)/psycopg2-$(PKG_VERSION)
PKG_BUILD_DEPENDS:=python libpq python/host

include $(INCLUDE_DIR)/package.mk
$(call include_mk, python-package.mk)
$(call include_mk, python3-package.mk)

define Package/python-psycopg2/Default
  SUBMENU:=Python
  SECTION:=lang
  CATEGORY:=Languages
  URL:=http://www.initd.org/
  DEPENDS:=+libpq
endef

define Package/python-psycopg2
$(call Package/python-psycopg2/Default)
  TITLE:=PostgreSQL database adapter for Python
  DEPENDS:=+PACKAGE_python-psycopg2:python +PACKAGE_python-psycopg2:python-egenix-mx-base
endef

define Package/python3-psycopg2
$(call Package/python-psycopg2/Default)
  TITLE:=PostgreSQL database adapter for Python3
  DEPENDS:=+PACKAGE_python3-psycopg2:python3 +PACKAGE_python3-psycopg2:python3-egenix-mx-base
endef

define Package/python-psycopg2/description
Psycopg is the most popular PostgreSQL adapter for the Python programming language
endef

define Package/python3-psycopg2/description
$(call Package/python/psycopg2/description)
.
(Variant for Python3)
endef

define Build/Compile
	# The PATH var is required so that psycopg2's setup.py script finds pg_config
	$(call Build/Compile/PyMod,., \
		install --prefix=/usr --root=$(PKG_INSTALL_DIR), \
		PATH=$(STAGING_DIR)/usr/bin:$(PATH))
endef

define Package/python-psycopg2/install
	$(INSTALL_DIR) $(1)$(PYTHON_PKG_DIR)
	$(CP) \
	    $(PKG_INSTALL_DIR)$(PYTHON_PKG_DIR)/* \
	    $(1)$(PYTHON_PKG_DIR)
endef

define Package/python3-psycopg2/install
	$(INSTALL_DIR) $(1)$(PYTHON3_PKG_DIR)
	$(CP) \
	    $(PKG_INSTALL_DIR)$(PYTHON3_PKG_DIR)/* \
	    $(1)$(PYTHON3_PKG_DIR)
endef

$(eval $(call PyPackage,python-psycopg2))
$(eval $(call BuildPackage,python-psycopg2))
$(eval $(call Py3Package,python3-psycopg2))
$(eval $(call Build3Package,python3-psycopg2))
