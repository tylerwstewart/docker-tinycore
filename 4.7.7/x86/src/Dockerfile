FROM busybox

ADD tce-load.patch /tmp/
RUN wget http://www.tinycorelinux.net/4.x/x86/release/distribution_files/core.gz \
    && mkdir rootfs \
    && cd rootfs \
    && gzip -dc ../core.gz | cpio -id \
    && rm -f ../core.gz \
    && cd usr/bin \
    && patch < /tmp/tce-load.patch \
    && cd ../.. \
    && rm -f /tmp/tce-load.patch \
    && tar cf - . | gzip -c > /tmp/rootfs.tar.gz \
    && cd .. \
    && rm -rf rootfs

CMD ["/bin/true"]
