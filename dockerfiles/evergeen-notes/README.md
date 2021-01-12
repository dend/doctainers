# Evergreen Notes

See [blog post](https://den.dev/blog/evergreen-notes/) for details. The image is also available on [Docker Hub](https://hub.docker.com/r/dend/hugo-notes).

## Running

An example of running the container on Windows:

```powershell
docker run -it -p 80:1900 -v /D/kb/content:/hugotools/site/content -v /D/kb/config.toml:/hugotools/site/config.toml CONTAINER_HASH
```