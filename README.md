# docker-notes
## References
- [Docker Mastery Course by Bret Fischer on Udemy](https://www.udemy.com/course/docker-mastery/) - Great Course, go for it first. Use below for reference.
- [www.docker.com documentation](https://docs.docker.com/)
### prune and df

[Demo video](https://youtu.be/_4QzP7uwtvI)
- `docker system df` - tells space usage. breaks down where are space is used up - images, containers, volume.
- `docker image prune` - cleans dangling images
- `docker container prune` - cleans all stopped containers
- `docker system prune` - cleans everything 
    - all stopped containers
    - all volumes not used by atleast one container
    - all networks not used by atleast one container
    - all dangling images (dangling images are all the layers that don't have relation with your existing images.)
- `docker system prune -a` - cleans everything not just dangling images, stopped containers, unused volumes. 

### docker and persistent data
docker.com reference on mounts.(https://docs.docker.com/storage/)
- Containers are immutable(can't be changed at runtime) and ephemeral(once removed, data loss happens). 
- This is not a limitation but a design goal "immutable infrastructure"(means only redeploy, never change). Gives reliability and consistency i.e. change is reproducible
- But Containers may create data that would be required to be persisted like databases, files, etc.
- Docker ensures "Seperation of Concerns" i.e. docker images just hold binaries and immutable data however other concerns like "PERSISTENT DATA"(databases, or unique data produced in other forms) are seperated
- Solution for Persistent Data  - VOLUMES, BIND MOUNT

### volumes
https://docs.docker.com/engine/reference/builder/#volume
- configuration option that make special location outside of container UFS(Union File System) to allow to save unique data.
- preserves data across container removals and allows to attach to any new containers.
- containers see it as local file path.
- any data that is created by container outlives until volume is deleted manually.
> Dockerfile Usage
`VOLUME ["/data"]`

### bindmounts
- sharing or mounting host directory or file onto the container
- link container path to host path
- containers see it as local file path.




