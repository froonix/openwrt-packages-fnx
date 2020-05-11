include $(TOPDIR)/rules.mk

PKG_NAME:=roundabout
PKG_SNAPSHOT:=66761fa
PKG_VERSION:=0.1.4
PKG_RELEASE:=4
PKGARCH:=all

PKG_CAT:=xzcat
PKG_SOURCE:=$(PKG_NAME)-$(PKG_SNAPSHOT).tar.xz
PKG_SOURCE_URL:=https://github.com/froonix/openwrt-stuff/releases/download/$(PKG_NAME)-$(PKG_VERSION)/
PKG_HASH:=8147f3a040e5952d083e8bed99ac375b76aef9f804a53cde6bfa4485dbe5e36d
PKG_BUILD_DIR:=$(BUILD_DIR)/$(PKG_NAME)-$(PKG_SNAPSHOT)

PKG_MAINTAINER:=Christian Schrötter <cs@fnx.li>
#PKG_LICENSE:=GPL-3.0-or-later
#PKG_LICENSE_FILES:=LICENSE

include $(INCLUDE_DIR)/package.mk

define Package/roundabout
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
* OpenDNS hostname updates: Use DynDNS to update the IP addresses.

There's full IPv6 support for all features! (excluding OpenDNS stuff...)
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
