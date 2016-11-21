FROM scratch
ADD rootfs.tar.gz /
ADD squashfs-tools.tar.gz /

ENV USER="tc" LANGUAGE="C.UTF-8" LANG="C.UTF-8"

# Keymap?
#~ [ -n "$KEYMAP" ] || KEYMAP="us"
#~ if [ -f "/usr/share/kmap/$KEYMAP.kmap" ]; then
	#~ echo -n "${GREEN}Setting keymap to ${MAGENTA}$KEYMAP"
	#~ /sbin/loadkmap < /usr/share/kmap/$KEYMAP.kmap
	#~ echo "KEYMAP=$KEYMAP" > /etc/sysconfig/keymap
	#~ echo "${GREEN} Done.${NORMAL}"
#~ fi

RUN mkdir -p /tmp/tce/optional /tmp/tcloop /usr/local/tce.installed \
    && echo "LANG=$LANGUAGE" > /etc/sysconfig/language \
    && chown -R root:staff /tmp/tce \
    && chgrp -R staff /dev /home /mnt /opt /run /tmp /var \
          /usr/local/tce.installed /etc/sysconfig /etc/skel \
          /etc/[gnpr]* /etc/host.conf /etc/issue /etc/inittab \
    && chgrp staff /etc/init.d \
    && chmod -R u+rwX,g+rwX /tmp/tce /usr/local/tce.installed /tmp/tcloop \
    && ln -sf /tmp/tce /etc/sysconfig/tcedir \
    && echo -n tc > etc/sysconfig/tcuser \
    && . /etc/init.d/tc-functions \
    && setupHome \
    && chmod u+s /bin/busybox /usr/bin/sudo 

USER tc
CMD ["/bin/sh"]
