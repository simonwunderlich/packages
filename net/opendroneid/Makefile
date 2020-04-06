include $(TOPDIR)/rules.mk

PKG_NAME:=opendroneid
PKG_SOURCE_VERSION:=825f5df8a3874d15f3f7d16284face9c492ab236
PKG_VERSION:=2020-04-06-$(PKG_SOURCE_VERSION)
PKG_RELEASE:=1

PKG_SOURCE_PROTO:=git
PKG_SOURCE_URL:=https://github.com/opendroneid/opendroneid-core-c.git
PKG_MIRROR_HASH:=5b225baff9f8632a30438e2c2671d0f600b2a795ca1cf432b42e0d0e8f2556b4

PKG_SOURCE:=$(PKG_NAME)-$(PKG_VERSION).tar.bz2
PKG_SOURCE_SUBDIR:=$(PKG_NAME)-$(PKG_VERSION)

include $(INCLUDE_DIR)/package.mk
include $(INCLUDE_DIR)/cmake.mk

TARGET_CFLAGS += -I$(STAGING_DIR)/usr/include -I${STAGING_DIR}/usr/include/libnl-tiny
CMAKE_OPTIONS += -DBUILD_MAVLINK=off

define Package/$(PKG_NAME)
	SECTION:=net
	CATEGORY:=Network
	DEPENDS:=+libgps +libnl-tiny
	TITLE:=OpenDroneID Reference implementation for WiFi
endef

define Package/$(PKG_NAME)/description
	This is the sender part of the reference implementation of the OpenDroneID protocol for WiFi.
endef

define Package/$(PKG_NAME)/install
	$(INSTALL_DIR) $(1)/usr/lib
	$(CP) $(PKG_BUILD_DIR)/libopendroneid/libopendroneid.so $(1)/usr/lib/
	$(INSTALL_DIR) $(1)/usr/bin
	$(INSTALL_BIN) $(PKG_BUILD_DIR)/wifi/sender/sender $(1)/usr/bin/odid_sender
	$(CP) ./files/* $(1)/
endef

$(eval $(call BuildPackage,$(PKG_NAME)))
