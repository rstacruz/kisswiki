- https://coreos.com/docs/launching-containers/launching/getting-started-with-systemd/

`systemctl --help`

## list unit files

`systemctl list-unit-files`

## reread unit files

`systemctl daemon-reload`

http://serverfault.com/questions/700862/do-systemd-unit-files-have-to-be-reloaded-when-modified

## start service

`sudo systemctl start mongod`

## load during startup

`sudo systemctl enable mongod`

## status

`sudo systemctl status mongod`
