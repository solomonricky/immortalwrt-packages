include $(TOPDIR)/rules.mk

PKG_NAME:=aardvark-dns
PKG_VERSION:=1.12.2
PKG_RELEASE:=1

PKG_SOURCE:=$(PKG_NAME)-$(PKG_VERSION).tar.gz
PKG_SOURCE_URL:=https://codeload.github.com/containers/aardvark-dns/tar.gz/v$(PKG_VERSION)?
PKG_HASH:=19317d97525c19135b31f76101b9c13bf2b009cecfc11f467b2ab30fb2641867

PKG_MAINTAINER:=Oskari Rauta <oskari.rauta@gmail.com>
PKG_LICENSE:=Apache-2.0
PKG_LICENSE_FILES:=LICENSE
PKG_CPE_ID:=cpe:/a:containers:aardvark-dns

PKG_BUILD_DEPENDS:=rust/host
PKG_BUILD_PARALLEL:=1

include $(INCLUDE_DIR)/package.mk
include ../../lang/rust/rust-package.mk

define Package/aardvark-dns
  SECTION:=net
  CATEGORY:=Network
  DEPENDS:=$(RUST_ARCH_DEPENDS)
  TITLE:=authoritative dns server for container records
  URL:=https://github.com/containers/aardvark-dns
endef

define Package/aardvark-dns/description
  Aardvark-dns is an authoritative dns server for A/AAAA container records.
  It can forward other requests to configured resolvers.

  It is mostly intended to be used with Netavark which will
  launch it automatically if both are installed.
endef

define Package/aardvark-dns/install
	$(INSTALL_DIR) $(1)/usr/lib/podman
	$(INSTALL_BIN) $(PKG_INSTALL_DIR)/bin/aardvark-dns $(1)/usr/lib/podman/
endef

$(eval $(call RustBinPackage,aardvark-dns))
$(eval $(call BuildPackage,aardvark-dns))
