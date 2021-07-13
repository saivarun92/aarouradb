sourcecred_profile=devtest    #source account aws credentails profilename
 region=us-east-2              #aws sourcedb region information
 targetregion=us-east-2        #target account region information
 snapshotname=saitest13        #name of the snapshot we need to create
 sourceclustername=lims-anc-tst  #source db name which we want to take snapshot
 target_awsaccountid=598430799738    #target aws account id number
 source_awsaccountid=238329888963                # we need to difne source aws account id number
 targetcred_profile=sandbox          #target account aws credentailsprofilename
 newcopy-snapshotname=copyfromshared-test   #target aws account name of the snapshot from sharedsnapshot
 kmsid=arn:aws:kms:us-east-2:122511138117:key/88bb6975-bed2-41d3-97b1-1a50baaab91d   #kmsiddetails
 rds_action=take_rds_snapshot 
 


ansible-playbook my_app_backup.yaml -i inventories/poc/hosts \ 
--extra-vars "sourcecred_profile=devtest region=us-east-2 rds_action=take_rds_snapshot targetregion=us-east-2 snapshotname=saitest13 \
 sourceclustername=lims-anc-tst  target_awsaccountid=598430799738 source_awsaccountid=238329888963  targetcred_profile=sandbox \
 newcopy-snapshotname=copyfromshared-test kmsid=arn:aws:kms:us-east-2:122511138117:key/88bb6975-bed2-41d3-97b1-1a50baaab91d rds_action=take_rds_snapshot" -vvv

