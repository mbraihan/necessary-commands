# Necessary-commands

Below here is the necessary commands for day-to-day works of all kind.

## Copying a file or Directory over ssh

A simpler method that works with via SSH controlled computers is to connect with SFTP (SSH File Transfer Protocol).]

1. cd to where you want the file saved

$ cd Dataset

2. Establish connection

$ sftp username@server_ip_or_remote_hostname

3. Go the directory that contains the file to be transferred.

$ cd Work/dataset/

4. To get the file

$ get data.txt

5. To get the complete directory

$ get -r files/