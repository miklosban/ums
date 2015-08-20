# ums

This is a simple repository/version control managaer
I'm using it for manage uploadings to web servers 
instead of using ftp or scp files to remote hosts

It is also using scp however it have some useful functionalities:
get the current version from the server and put it a local folder (.UMS_REPOSITORY)
put the files to the remote server to the appropriate remote directory 

It is using a simple config file for the remote server/remote directory structure

The idefault config file path is .ums_projects

the syntax like:

[foo]
PROJECT_NAME=foo
REMOTE_URL=www.foo.com
REMOTE_USER=miki
REMOTE_PATH=/var/www/foo/
LOCAL_PATH=foo
PARALLEL=0

[bar]
PROJECT_NAME=bodobacs
REMOTE_URL=www.bar.org
REMOTE_USER=banmiki
REMOTE_PATH=/var/www/html/bar/
LOCAL_PATH=bar
PARALLEL=0

The REMOTE_PATH is simple. It is an absolute path.
The LOCAL_PATH is used the cut the path from the project directory structure and this path subset will append to the REMOTE_PATH
The method assumes that the two project direcory structure is matching.

E.g.: I have a ~/WEB direcory with several projects: WEB/foo WEB/bar
I would like to upload some file to the foo project's js directory
I'm going to the ~/WEB/foo/js folder
and I upload the foo.js file to the foo project:
uploader foo.js foo

The LOCAL_PATH is foo therefore it cut '/js' path
and will try to get from the "www.foo.com" server the /var/www/foo/js/foo.js file.
and will try to put to the "www.foo.com" server the /var/www/foo/js/foo.js file.

Both actions will be strored in the UMS_REPOSITORY/repository.db
and the remote file will stored in the UMS_REPOSITORY/123__foo.js
The numbers incremented automatically.

If there are comments passed, these will be stored in the repository.db.

The repository.db not used any more. Not really necessary ...
