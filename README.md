# srp-boot - Mount SRP devices in initramfs, using a sBFT (SRP Boot Firmware Table)

Run srp-boot in your initramfs, before it tries to use your SRP devices.

Requires:
* Your initramfs to load your HCA driver(s) before running.
* Modprobe to find these kernel modules in your initramfs: ib_sbft, ib_core, ib_umad, ib_uverbs, ib_ucm, rdma_ucm, and ib_srp.

These should never be needed, but two optional kernel arguments are supported in case auto-detection fails.  srp-boot should always be able to detect the hca and port number that match the sBFT's ib_source_gid.
* "srp.hca=<HCA>", where HCA is the device name in /sys/class/infiniband_srp/srp-<DEVICE_NAME>-<PORT_NUMBER>, typically the same device name as shown in /sys/class/infiniband/.
* "srp.port_number=<PORT_NUMBER>", where PORT_NUMBER is the port number in /sys/class/infiniband_srp/srp-<DEVICE_NAME>-<PORT_NUMBER>, typically the same port number as shown in /sys/class/infiniband/<HCA>/ports/, that you're using elsewhere.
