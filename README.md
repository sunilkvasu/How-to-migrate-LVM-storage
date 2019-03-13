# How-to-migrate-LVM-storage

lvs --segments

lvs -o+devices

pvcreate /dev/sdc

vgextend vg_data /dev/sdc

lvconvert -m1 vg_data/lv_opt_data /dev/sdc

lvconvert -m0 vg_data/lv_opt_data /dev/sdb

