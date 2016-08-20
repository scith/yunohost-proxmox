
BASEDIR:=$(shell dab basedir)

all: info/init_ok
	dab bootstrap --minimal
	dab install git
	dab exec git clone https://github.com/YunoHost/install_script /tmp/install_script
	dab exec cd /tmp/install_script; sudo ./install_yunohost -a
	sed -e 's/^PermitRootLogin without-password/PermitRootLogin yes/' -i ${BASEDIR}/etc/ssh/sshd_config
	dab finalize

info/init_ok: dab.conf
	dab init
	touch $@

.PHONY: clean
clean:
	dab clean
	rm -f *~

.PHONY: dist-clean
dist-clean:
	dab dist-clean
	rm -f *~

