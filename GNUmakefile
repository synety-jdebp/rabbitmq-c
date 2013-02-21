include Makefile

PACKAGE_FILES = usr/local/include/*.h usr/local/lib/lib* usr/local/bin/*

.PHONY: package

package: librabbitmq-synety_1.0.deb

librabbitmq-synety_1.0.deb: debian-binary control.tar.gz data.tar.gz
	${AR} rc $@.tmp $^
	mv $@.tmp $@

data.tar.gz: ${PACKAGE_FILES}
	tar --create --gzip --file $@.tmp usr
	mv $@.tmp $@

control.tar.gz: control md5sums
	tar --create --gzip --file $@.tmp $^
	mv $@.tmp $@

md5sums: ${PACKAGE_FILES}
	md5sum -- $^ > $@.tmp
	mv $@.tmp $@

