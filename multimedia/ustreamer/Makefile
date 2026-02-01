#
# This is free software, licensed under the GNU General Public License v2.
# See /LICENSE for more information.
#

include $(TOPDIR)/rules.mk

PKG_NAME:=ustreamer
PKG_VERSION:=6.50
PKG_RELEASE:=1
PKG_MAINTAINER:=Georgi Valkov <gvalkov@gmail.com>

PKG_SOURCE:=$(PKG_NAME)-$(PKG_VERSION).tar.gz
PKG_SOURCE_URL:=https://codeload.github.com/pikvm/ustreamer/tar.gz/v$(PKG_VERSION)?
PKG_HASH:=0cd365197954d7724fc33b5daf0d15adc5577be256e0b57fb1c721aa2e3fce23
PKG_UNPACK=$(HOST_TAR) -C $(PKG_BUILD_DIR) --strip=2 -xf $(DL_DIR)/$(PKG_SOURCE)

PKG_LICENSE:=GPL-3.0
PKG_LICENSE_FILES:=LICENSE

include $(INCLUDE_DIR)/package.mk

define Package/ustreamer
	SECTION:=multimedia
	CATEGORY:=Multimedia
	TITLE:=uStreamer
	DEPENDS:=+libatomic +libjpeg +libevent2 +libevent2-pthreads
	URL:=https://github.com/pikvm/ustreamer
endef

define Package/ustreamer/description
	µStreamer - Lightweight and fast MJPEG-HTTP streamer
endef

define Package/ustreamer/install
	$(INSTALL_DIR) $(1)/usr/bin
	$(INSTALL_BIN) $(PKG_BUILD_DIR)/ustreamer.bin $(1)/usr/bin/ustreamer
	$(INSTALL_BIN) $(PKG_BUILD_DIR)/ustreamer-dump.bin $(1)/usr/bin/ustreamer-dump
	$(INSTALL_DIR) $(1)/etc/config
	$(INSTALL_CONF) ./files/ustreamer.config $(1)/etc/config/ustreamer
	$(INSTALL_DIR) $(1)/etc/init.d
	$(INSTALL_BIN) ./files/ustreamer.init $(1)/etc/init.d/ustreamer
	$(INSTALL_DIR) $(1)/etc/hotplug.d/usb
	$(INSTALL_DATA) ./files/ustreamer.hotplug $(1)/etc/hotplug.d/usb/20-ustreamer
endef

$(eval $(call BuildPackage,ustreamer))
