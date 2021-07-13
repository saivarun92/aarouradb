PLaybook-1 variables

snapshotname
target_account
rds_action=take_rds_snapshot   
region
sourcename= lims-anc-tst

AWS_PROFILE=dev ansible-playbook my_app_backup.yaml -i inventories/poc/hosts --extra-vars "rds_action=take_rds_snapshot sourcename=lims-anc-tst snapshotname=saitest13 target_account=598430799738 region=us-east-2" -vvv


