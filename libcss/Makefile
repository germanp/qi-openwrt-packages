include $(TOPDIR)/rules.mk

PKG_NAME:=libcss
PKG_VERSION:=0.1.0
PKG_RELEASE:=1

PKG_SOURCE:=$(PKG_NAME)-$(PKG_VERSION)-src.tar.gz
PKG_SOURCE_URL:=http://www.netsurf-browser.org/projects/releases/
PKG_BUILD_DIR:=$(BUILD_DIR)/$(PKG_NAME)-$(PKG_VERSION)-src

include $(INCLUDE_DIR)/package.mk

define Package/libcss
	MAINTAINER:="Xiangfu Liu" <xiangfu@sharism.cc>
	SECTION:=libs
	CATEGORY:=Libraries
	TITLE:=LibCSS is a CSS parser and selection engine, written in C
	URL:=http://www.netsurf-browser.org/projects/libcss/
	DEPENDS:=+libparserutils +libwapcaplet
endef

define Package/libcss/description
	LibCSS is a CSS parser and selection engine, written in C. It aims to parse the forward compatible CSS grammar. It was developed as part of the NetSurf project
endef

define Build/Compile
	rm -rf $(PKG_INSTALL_DIR)
	$(MAKE_VARS) $(MAKE) -C $(PKG_BUILD_DIR) \
		$(MAKE_FLAGS) \
		WARNFLAGS="" \
		COMPONENT_TYPE=lib-shared \
		DESTDIR="$(PKG_INSTALL_DIR)" \
		HOST_CC=gcc \
		all install
endef

define Build/InstallDev
	mkdir -p $(1)/usr/include
	$(CP) $(PKG_INSTALL_DIR)/usr/local/include/* $(1)/usr/include/
	mkdir -p $(1)/usr/lib
	$(CP) $(PKG_INSTALL_DIR)/usr/local/lib/* $(1)/usr/lib/
endef

define Package/libcss/install
	$(INSTALL_DIR) $(1)/usr/lib
	$(CP) $(PKG_INSTALL_DIR)/usr/local/lib/libcss.so* $(1)/usr/lib/
endef

$(eval $(call BuildPackage,libcss))
