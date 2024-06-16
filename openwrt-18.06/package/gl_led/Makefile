include $(TOPDIR)/rules.mk

PKG_NAME:=gl_led
PKG_VERSION:=1.0
PKG_RELEASE:=1

include $(INCLUDE_DIR)/package.mk

define Package/gl_led
	SECTION:=utils
	CATEGORY:=Utilities
	TITLE:=Gl led service
	DEPENDS:=+bash
	MAINTAINER:=ZIM555 <zeustreker@gmail.com>
endef

define Package/gl_led/description
	This package installs a gl_led service.
endef

define Build/Compile
	# Nothing to compile for this package
	true
endef

define Package/gl_led/install
	$(INSTALL_DIR) $(1)/etc/init.d
	$(INSTALL_BIN) ./files/etc/init.d/gl_led $(1)/etc/init.d/gl_led
	$(INSTALL_DIR) $(1)/etc/config
	$(INSTALL_CONF) ./files/etc/config/gl $(1)/etc/config/gl
endef

$(eval $(call BuildPackage,gl_led))