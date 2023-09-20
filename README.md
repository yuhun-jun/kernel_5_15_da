# Project Overview

This project focuses on researching performance degradation caused by file fragmentation. The codebase is branched from Linux Kernel 5.15.0, and it aims to enhance performance by modifying the filesystem, block layer, and NVMe device driver. These modifications enable the transmission of filesystem-level append and overwrite information to NVMe commands.

## Modified Files
All changes are annotated with "//2448" before and after.

### Filesystem and Block Layer

#### block/bio.c
- Verified if the filesize has changed.

#### fs/ext4/inode.c
- Checked for changes in filesize.

#### include/linux/page-flags.h
- Monitored filesize changes.

#### fs/ext4/page-io.c
- Examined extent status and stored additional information in the bio.

#### include/trace/events/mmflags.h
- Added 'filesizechanged' to map flags.

#### block/blk-core.c
- Initialized requests.

#### block/blk-mq.c
- Recorded additional information in requests.

#### fs/ext4/inode.c
- Monitored block count changes.

#### include/linux/blk_types.h
- Added information to the bio structure.

#### include/linux/blkdev.h
- Added information to the request structure.

### Device Driver

#### drivers/nvme/host/core.c
- Incorporated information into NVMe commands based on request details.

#### drivers/nvme/host/trace.h
- Added debugging information to the NVMe command log.

#### include/linux/nvme.h
- Added information to the NVMe command structure.


