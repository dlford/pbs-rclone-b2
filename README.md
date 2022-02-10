# PBS Rclone B2

Syncs a Proxmox Backup Server directory (Or any directory, actually) with a B2 bucket

## Setup

1. Install `solo` and `sync-b2` in your path of choice (`/usr/local/bin/` is a good option).
2. Edit the variables in `sync-b2` (example below).
3. Add `/usr/local/bin/sync-b2` to a crontab entry.

```txt
SOLO_BIN="/usr/local/bin/solo"
RCLONE_BIN="/usr/bin/rclone"
RCLONE_CONF_DIR="/home/USER/.config/rclone/rclone.conf"
SOLO_PORT="6000"
SYNC_ARGS="--create-empty-src-dirs --log-file=/var/log/sync-b2.log --log-level=INFO --bwlimit 10M"
SRC_PATH="/mnt/datastore/BACKUP_STORAGE_NAME"
DEST_STORE="STORAGE_FROM_RCLONE_CONFIG"
DEST_PATH="BUCKET_NAME/PATH/TO/TARGET"
```

_Note: If you keep the `log-file` in args, consider adding it to `logrotate` or switching the log level, it can get pretty big on `log-level=INFO`_
