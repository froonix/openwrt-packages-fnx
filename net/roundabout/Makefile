include $(TOPDIR)/rules.mk

PKG_NAME:=roundabout
PKG_SNAPSHOT:=0cfd05a
PKG_VERSION:=0.2.1
PKG_RELEASE:=1

PKG_CAT:=xzcat
PKG_SOURCE:=$(PKG_NAME)-$(PKG_SNAPSHOT).tar.xz
PKG_SOURCE_URL:=https://github.com/froonix/openwrt-stuff/releases/download/$(PKG_NAME)-$(PKG_VERSION)/
PKG_HASH:=ca2e0880f5ad4338d2a060a73296a268068e770788358248cd9439151c80b33f
PKG_BUILD_DIR:=$(BUILD_DIR)/$(PKG_NAME)-$(PKG_SNAPSHOT)

PKG_MAINTAINER:=Christian Schrötter <cs@fnx.li>
#PKG_LICENSE:=GPL-3.0-or-later
#PKG_LICENSE_FILES:=LICENSE

include $(INCLUDE_DIR)/package.mk

define Package/roundabout
  PKGARCH:=all
  SECTION:=net
  CATEGORY:=Network
  SUBMENU:=Routing and Redirection
  TITLE:=Roundabout routing helper script
  URL:=https://github.com/froonix/openwrt-stuff
endef

define Package/roundabout/description
This script is a helper script for the following purposes:

* Restart services (daemons) or networks (interfaces) on ifup/ifdown.
* Policy-Based Routing (PBR): Setup rules and tables for source addresses.
* LED management (routing): Enable or disable leds on default route change.
* LED management (link layer): Enable or disable leds on ifup/ifdown.

There's full IPv6 support for all features!
endef

define Build/Configure
	true
endef

define Build/Compile
	true
endef

define Package/roundabout/conffiles
/etc/config/roundabout
endef

define Package/roundabout/install
	$(INSTALL_DIR) $(1)/etc/config
	$(INSTALL_DIR) $(1)/etc/hotplug.d/iface
	$(INSTALL_DATA) $(PKG_BUILD_DIR)/etc/config/roundabout $(1)/etc/config/roundabout
	$(INSTALL_BIN) $(PKG_BUILD_DIR)/etc/hotplug.d/iface/60-roundabout $(1)/etc/hotplug.d/iface/60-roundabout
endef

$(eval $(call BuildPackage,roundabout))
