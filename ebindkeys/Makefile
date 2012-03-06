include $(TOPDIR)/rules.mk

PKG_NAME:=ebindkeys-zipit
PKG_VERSION:=2010.12.22
PKG_REV:=1
PKG_RELEASE:=1
PKG_INSTALL:=1

PKG_SOURCE:=$(PKG_NAME)-$(PKG_VERSION).tar.bz2
PKG_SOURCE_URL:=http://home.vay8.net/_media/
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
