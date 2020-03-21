# docker-notes

### prune and df

[Demo video](https://youtu.be/_4QzP7uwtvI)
- `docker system df` - breaks down where are space is used up - images, containers, volume.
- `docker image prune` - cleans dangling images
- `docker container prune` - cleans all stopped containers
- `docker system prune` - cleans everything 
    - all stopped containers
    - all volumes not used by atleast one container
    - all networks not used by atleast one container
    - all dangling images (dangling images are all the layers that don't have relation with your existing images.)
- `docker system prune -a` - cleans everything not just dangling images, stopped containers, unused volumes. 

