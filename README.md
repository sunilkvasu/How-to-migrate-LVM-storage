# How-to-migrate-LVM-storage

df -hP /opt/data

lvs --segments

lvs -o+devices

vgs -o+devices

pvs

echo "- - -" > /sys/class/scsi_host/host3/scan

pvcreate /dev/sdc

vgextend vg_data /dev/sdc

lvconvert -m1 vg_data/lv_opt_data /dev/sdc

lvconvert -m0 vg_data/lv_opt_data /dev/sdb

vgreduce vg_data /dev/sdb

pvremove /dev/sdb

