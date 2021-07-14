

ENVIRONMENT VARIBAES
==================================================
1)Step1: adding the aws source and target credentials to the machine where we are executing this playbooks

vim ~/.aws/config

##this is source aws account this is optional
[default]
region = us-east-2
output = json

##this is source aws account 
[profile devtest]
region = us-east-2
output = json

##this is target aws account
[profile sandbox]
region = us-east-2
output = json


vim ~/.aws/credentails

##this is source aws account credentials this is optional
[default]
aws_access_key_id=******************
aws_secret_access_key=*******************
aws_session_token=*****************************

##this is source aws account credentials
[devtest]
aws_access_key_id=******************
aws_secret_access_key=*******************
aws_session_token=*****************************

##this is target aws account credentials
[sandbox]
aws_access_key_id=******************
aws_secret_access_key=*******************
aws_session_token=*****************************

===========================================================================================
2)Step2:
we need to login the source account and identfy the which rds db which we need to work
once identify the dbname check the KMS key of that db, navigate to kms key and update the KMS policy

3)Step3:

##############################################################
 PARAMETERS
#########################################################################
 sourcecred_profile=devtest    #source account aws credentails profilename
 region=us-east-2              #aws sourcedb region information
 targetregion=us-east-2        #target account region information
 snapshotname=saitest13        #name of the snapshot we need to create
 sourceclustername=lims-anc-tst  #source db name which we want to take snapshot
 target_awsaccountid=598430799738    #target aws account id number
 source_awsaccountid=238329888963                # we need to difne source aws account id number
 targetcred_profile=sandbox          #target account aws credentailsprofilename
 newcopy-snapshotname=copyfromshared-test   #target aws account name of the snapshot from sharedsnapshot
 kmsid=arn:aws:kms:us-east-2:598430799738:key/0d4b8594-24d0-4ecd-aa7e-371659a22e2b   #kmsiddetails
 rds_action=take_rds_snapshot   # this the role name
 targetclusterdbname= test-dbname    ##this is the targetdbname what we want to install from snapshot in target machine
 targetdbinstancename= test-db-instace   ## this the the target instance name unsder the targetclustername in target machine
 
 

woring Ansible
============================================

ansible-playbook my_app_backup.yaml -i inventories/poc/hosts \
--extra-vars "sourcecred_profile=devtest region=us-east-2 rds_action=take_rds_snapshot \
targetregion=us-east-2 snapshotname=sai-test-13 sourceclustername=lims-anc-tst \
target_awsaccountid=598430799738 source_awsaccountid=238329888963  targetcred_profile=sandbox \
newcopysnapshotname=copy-sai-test-13 kmsid=arn:aws:kms:us-east-2:238329888963:key/0a108b6d-0323-4904-8d2f-4f2032160808 \
targetclusterdbname=testclusterdb-sai-13 targetdbinstancename=testdbinstace-sai-13" -vvv



####################################################################
########################################################################
############################################
#restoring clusterdb
############################################

