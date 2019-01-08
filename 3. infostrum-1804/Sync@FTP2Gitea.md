# Sync from FTP to Gitea
## Specification
- The project owner is not us, and the owner only open the FTP to us, but the owner and we both can do changes in this FTP.
- So, it means the repo in our hands are not master version, we always need to sync(daily) the latest version before doing changes.

## First of all
- First, we need a repo on Gitea for FTP project.
- After creating repo on Gitea, we need to init a local repo on Linux server.
  - e.g. I choose the directory `/var/xxx/` for the project
  - then `git clone http://username:password@{url}`
> The reason why put `username` and `password` in front of the url is that if we do, it doesn't ask for authorization every time when we do push or pull.

## Sync from ftp
- Now we have a empty local repo on Linux server, and be ready to put project in.
- We use `lftp` wiget for the ftp sync feature
- the manual way to do is:

```shell
## for the connection
lftp open -u {ftpusername},{ftppassword} {host}
## for the sync
mirror {pathfromftp} {pathfromlocal}
```

- but we need to write into a `.sh` file for daily running:

```shell
HOST='{ftphost}'
USER='{ftpusername}'
PASSWORD='{ftppassword}!'

LOCAL_DIR='/var/probis'

lftp -u "$USER","$PASSWORD" "$HOST" <<EOF
mirror -x f/ / '$LOCAL_DIR'/
exit
EOF
```

- While inputing `lftp`, the system cmd will turn into lftp's cmd.
- So we use this approach `<<EOF...EOF`, it's called `Here Document`, means that it'll input the commands between first `EOF` and second one as a document.
- And we use `-x {directory}` to exclude directory

## Update repo on Gitea
- We use `git` for sure, but you need to be aware of the identity to do these updates.
  - If you're first time doing this, you might not set up the `git` config (username & useremail)
  - When you do updates, `git` will take the hostname(`root`) for you.
  - So remember to set up the username by `git config --global user.name {yourname}`, and the email by `git config --global user.email {theemail}` as well.

```
## lftp commands above...
cd $LOCAL_DIR
git add .
git commit -m "(^) sync from ftp"
git pull
git push
```

## The Last: Running Task in Schedule
- We use `crontab` for task schedule
- Before setting up schedule, move to the `.sh` to `/var/task_schedule/{repo}/`
- So how to `crontab`? 
- `crontab [-u user] [-l | -r | -e] [-i]`
  - `-u user`: spcify the user to do
  - `-l`: list the current crontab
  - `-r`: remove the current crontab(**it means all the crons on crontab, so don't use it no matter what**)
  - `-e`: edit the current cribtab(**if you want to add, edit or remove crons, use this to do**)
  - `-i`: same as `-r`, but give a prompt to confirm yes/no
- the format of a cron

```sh
# Example of job definition:
# .---------------- minute (0 - 59)
# |  .------------- hour (0 - 23)
# |  |  .---------- day of month (1 - 31)
# |  |  |  .------- month (1 - 12) OR jan,feb,mar,apr ...
# |  |  |  |  .---- day of week (0 - 6) (Sunday=0 or 7) OR sun,mon,tue,wed,thu,fri,sat
# |  |  |  |  |
# *  *  *  *  * [user-name] [command to be executed]
```

- I don't specify username(no `-u user`), and use the `||` for multiple commands

```
0 21 * * * mkdir /var/task_schedule/xxx/`date +\%Y` || mkdir /var/task_schedule/xxx/`date +\%Y/\%m` || bash /var/task_schedule/xxx/ftp_sync_gitea_update.sh > /var/task_schedule/xxx/`date +\%Y/\%m/\%Y\%m\%d`.log
```

- e.g. the `xxx` project
  - it will start 21:00 everyday, and if today is 2018.05.30
  - make a directory to `/var/task_schedule/xxx/2018`(if it exists, skip)
  - make a directory to `/var/task_schedule/xxx/2018/05`(if it exists, skip)
  - execute the `sh` and output to `/var/task_schedule/xxx/2018/05/20180530.log`
