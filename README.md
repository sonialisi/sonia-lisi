# Personal Website

## Run Locally

```console
docker build . -t gh-website -f docker/Dockerfile
docker run --rm -p 4000:4000 gh-website
```