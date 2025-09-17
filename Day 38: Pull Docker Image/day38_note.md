Task: Pull busybox:musl image on App Server 3 in Stratos DC and re-tag (create new tag) this image as busybox:blog.

# Check images and re-tag ( create new tag )
docker images
docker tag busybox:musl busybox:blog