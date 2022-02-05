Goal: retrieve the contents of the `/etc/passwd` file from a vulnerability in the display of product images.

If an application requires that the user-supplied filename must start with the expected base folder, such as `/var/www/images`, then it might be possible to include the required base folder followed by suitable traversal sequences. For example:

`filename=/var/www/images/../../../etc/passwd`

For this, I simply used the following payload and appended it to the end of /images and retrieved /etc/passwd

/var/www/images/../../../etc/passwd

