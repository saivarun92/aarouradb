PLaybook-1 variables

snapshot-name
target_account
rds_action=take_rds_snapshot   
region


AWS_PROFILE=dev ansible-playbook my_app_backup.yaml -i inventories/poc/hosts -e rds_action=take_rds_snapshot snapshot-name=saitest13 target_account=598430799738 region=us-east-2 



PLAYV2
source-account=
snapshot-name
kmsid
newcopy-snapshotname
