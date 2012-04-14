include $(TOPDIR)/rules.mk

PKG_NAME:=ebindkeys-zipit
PKG_VERSION:=2012.04.12
PKG_REV:=f2a35ed6d96820c02ba806cbaab963e704c7c334
PKG_RELEASE:=1

PKG_SOURCE:=$(PKG_NAME)-$(PKG_VERSION)-$(PKG_REV).tar.gz
PKG_SOURCE_URL:=git://github.com/mozzwald/ebindkeys-zipit.git
PKG_SOURCE_PROTO:=git
PKG_SOURCE_SUBDIR:=$(PKG_NAME)-$(PKG_VERSION)
PKG_SOURCE_VERSION:=$(PKG_REV)
PKG_BUILD_DIR:=$(BUILD_DIR)/$(PKG_NAME)-$(PKG_VERSION)

include $(INCLUDE_DIR)/package.mk

define Package/ebindkeys
  SECTION:=utils
  CATEGORY:=Utilities
  TITLE:=ebindkeys, bind a key or key-combo to a command
  URL:=http://home.vay8.net/doku.php/?id=ebindkeys-zipit
  SUBMENU:=Terminal
endef

define Package/ebindkeys/description
	bind a key or key-combo to a command
endef

define Package/ebindkeys/install
	$(INSTALL_DIR) $(1)/usr/bin
	$(INSTALL_DIR) $(1)/etc/init.d
	$(INSTALL_BIN) $(PKG_BUILD_DIR)/ebindkeys $(1)/usr/bin/
	$(INSTALL_BIN) ./files/init.d/ebindkeys $(1)/etc/init.d/ebindkeys
	$(INSTALL_DATA) ./files/ebindkeysrc $(1)/etc
endef

define Package/ebindkeys/postinst
#!/bin/sh
# check if we are on real system
if [ -z "$${IPKG_INSTROOT}" ]; then
        echo "Enabling rc.d symlink for ebindkeys"
        /etc/init.d/ebindkeys enable
fi
exit 0
endef

define Package/ebindkeys/prerm
#!/bin/sh
# check if we are on real system
if [ -z "$${IPKG_INSTROOT}" ]; then
        echo "Removing rc.d symlink for mrelay"
        /etc/init.d/ebindkeys disable
fi
exit 0
endef

$(eval $(call BuildPackage,ebindkeys))
