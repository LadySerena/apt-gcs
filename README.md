# apt-transport-gcs

## APT Google Cloud Storage Transport

Allows one to use a private GCS Bucket as an APT repository.  Authentication is handled by `gcloud` tool locally or
by application default credentials on Google Compute Engine


## License

MIT - See LICENSE file

## Requirements

Working Go installation, if you don't have one see [Golang official help page](https://golang.org/doc/install)


This should build the gs binary for  amd64 Linux - change as needed
```
go get github.com/ceocoder/apt-gcs/cmd
env GOOS=linux GOARCH=amd64 go build -o gs github.com/ceocoder/apt-gcs/cmd
```

Copy generated binary `gs` to your `/usr/lib/apt/methods/` directory

Add the below to a `.list` file within the `/etc/apt/sources.list.d/` directory

```
deb gs://my-debs stable main
```

It will work with an APT repo generated by [reprepro](https://mirrorer.alioth.debian.org/) or [Aptly](https://www.aptly.info) and `gsutil rsync`ed to Google Cloud Storage
