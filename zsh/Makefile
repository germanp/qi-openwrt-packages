
include $(TOPDIR)/rules.mk

PKG_NAME:=zsh
PKG_RELEASE:=1
PKG_VERSION:=4.3.17
PKG_SOURCE_URL:=@SF/zsh
PKG_SOURCE:=zsh-$(PKG_VERSION).tar.bz2

include $(INCLUDE_DIR)/package.mk

define Package/zsh
  SECTION:=utils
  CATEGORY:=Utilities
  TITLE:=Shell designed for interactive use.
  DEPENDS:=+libncurses
  URL:=http://zsh.sourceforge.net/
endef

define Package/zsh/description
	Command line shell designed for interactive use and bash compatible.
endef

define Build/Configure
	$(call Build/Configure/Default)
endef

define Package/zsh/install
	make DESTDIR=$(1) -C $(PKG_BUILD_DIR) install
	$(INSTALL_DIR) $(1)/etc
	$(INSTALL_DATA) ./files/zshrc $(1)/etc/zshrc
endef

define Package/zsh/postinst
#!/bin/sh
grep zsh $${IPKG_INSTROOT}/etc/shells || \
        echo "/usr/bin/zsh" >> $${IPKG_INSTROOT}/etc/shells
endef

$(eval $(call BuildPackage,zsh))
