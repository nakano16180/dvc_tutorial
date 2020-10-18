## dvc_tutorial

### setup

```
$ cd dvc_tutorial/
$ pipenv install
```

### usage

```
add local dir to as remote
$ mkdir -p /tmp/dvc-storage
$ pipenv run dvc remote add -d myremote /tmp/dvc-storage

# update config
$ git commit .dvc/config -m "Configure local remote"

# push to remote
$ pipenv run dvc push
```

use minio

```
$ export AWS_ACCESS_KEY_ID="minioadmin"
$ export AWS_SECRET_ACCESS_KEY="minioadmin"

add minio as remote
$ pipenv run dvc remote add newremote s3://dvcstorage
$ pipenv run dvc remote modify newremote endpointurl http://localhost:9000
$ pipenv run dvc remote modify newremote use_ssl False

push to remote and commit config
$ pipenv run dvc push -r newremote
$ git commit .dvc/config -m "update configure minio"
```