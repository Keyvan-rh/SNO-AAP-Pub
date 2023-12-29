After installing AAP on your OCP you can use these 3 file to configuer the AAP to build a new SNO 
NOTE: To install AAP you need to have storage for postgres. On SNO you can install LVM operator, before installing the operator add new raw storage to the VM of the SNO. Then install the LVM operator and create LVM Cluster with all default values. after this is done you need to make the Storage class as default by adding new annotation "storageclass.kubernetes.io/is-default-class" and the value of ture.

use the following command to import these 3 files to your AAP:

1. aap-sno-all.json

     after this import you must update the password for all hosts and update github password with the correct tocken.

2. aap-sno-job-templates.json
3. aap-sno-workflow-templates.json



awx import --conf.host https://aap-ansible-automation-platform.apps.sno2.<your domain> --conf.username admin --conf.password  <<password>>  --conf.insecure < aap-sno-inventories.json

If you have change the setup and like to export the new config use the following commands:

awx export --conf.host https://aap-ansible-automation-platform.apps.sno1.<your domain> --conf.username admin --conf.password  <<password>> --conf.insecure --job_templates >> aap-sno-job-templates.json

awx export --conf.host https://aap-ansible-automation-platform.apps.sno1.<your domain> --conf.username admin --conf.password  <<password>> --conf.insecure  >> aap-sno-all.json
