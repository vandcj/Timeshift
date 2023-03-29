# System Backup and Restore

``` 
$ sudo apt update
$ sudo apt install timeshift
```

### Create and restore backup by using the Timeshift’s command line

#### Create a first backup simply by executing the below command:

``` $ sudo timeshift --create ```
###### The above command will also create a new configuration file located at the following location: /etc/timeshift.json.


#### The output will look something like this:
```
First run mode (config file not found)
Selected default snapshot type: RSYNC
Mounted '/dev/sda1' at '/run/timeshift/backup'
Selected default snapshot device: /dev/sda1
------------------------------------------------------------------------------
Estimating system size...
Creating new snapshot...(RSYNC)
Saving to device: /dev/sda1, mounted at path: /run/timeshift/backup
Synching files with rsync...
Created control file: /run/timeshift/backup/timeshift/snapshots/2023-03-29_07-47-39/info.json
RSYNC Snapshot saved successfully (55s)
Tagged snapshot '2023-03-29_07-47-39': ondemand
``` 


### List all your currently created system backup screenshots: 

``` $ sudo timeshift --list   ```

#### The output :

```
/dev/sda1 is mounted at: /run/timeshift/backup, options: rw,relatime,discard,errors=remount-ro

Device : /dev/sda1
UUID   : 9a7ad317-1eac-4f04-8300-403eacd3bd76
Path   : /run/timeshift/backup
Mode   : RSYNC
Status : OK
1 snapshots, 76.9 GB free

Num     Name                 Tags  Description
------------------------------------------------------------------------------
0    >  2023-03-29_07-47-39  O
``` 

### Restore from the backup snapshot: 

``` $ sudo timeshift --restore --snapshot "2023-03-29_07-47-39" ``` 

### Delete selected backup snapshot:

``` $ sudo timeshift --delete  --snapshot "2023-03-29_07-47-39" ``` 
