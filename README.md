# How-to-migrate-LVM-storage-online

# Migrate data from /dev/sdc to /dev/sdb

df -hP /opt/data

lvs --segments

lvs -o+devices

vgs -o+devices

pvs

echo "- - -" > /sys/class/scsi_host/host3/scan

pvcreate /dev/sdc

vgextend vg_data /dev/sdc

lvconvert -m1 vg_data/lv_opt_data /dev/sdb

lvconvert -m0 vg_data/lv_opt_data /dev/sdc

vgreduce vg_data /dev/sdb

pvremove /dev/sdb

echo "1" > /sys/class/block/sdb/device/delete
