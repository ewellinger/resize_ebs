# Resize EBS

The Purpose of this script is to resize the root Elastic Block Storage (EBS) of an already running AWS instance.  This is done using AWS CLI tools to stop the instance, detach the root volume, create a snapshot, make a new volume of a specified size using the old snapshot, reattach the new volume, and restart your instance.  Additional options can be provided to delete the old volume and/or snapshot following the completion of the script.

### SYNOPSIS
```sh
sh resize_ebs [vS] -i [instance-id] -s [size]   
```

The options are as follows:
* `-i [instancd-id]`
    * Specifies the Instance ID of the AWS instance to be resized
* `-s [size]`
    * Specifies the size, in GB, to resize the EBS to
* `-v`
    * Delete the old volume following the completion of the script
* `-S`
    * Delete the snapshot of the old volume following the completion of the script (you may wish to keep this until you are sure everything is working as intended)

### NOTE
This script makes a number of assumptions about how your system is configured including:
* You have the AWS CLI tools installed
* Your `~/.aws/config` file specifies the region that the instance you wish to resize is currently running on (you can set this with the `aws configure` command)
* Your pem file is located in `~/.ssh/`

You may also need to change the permissions of this script using the following command:
```sh
chmod +x resize_ebs
```
