# Put jellyfin Image
docker pull jellyfin/jellyfin
# Create dir for cache, config and media Volume
mkdir /pathtodir/cache
mkdir /pathtodir/config
mkdir /pathtodir/media
# Or careate volume
docker volume create jellyfin-cache
docker volume create jellyfin-cache
# Run jellyfin container
docker run \
-d \
--name jellyfinuser \
--user 1000:1000 \
--restart unless-stopped \
--volume /pathtodir/config:/config \
--volume /pathtodir/cache:/cache \
--mount type=bind,source=/pathtodir/media,target=/media \
-p 8096:8096 \
jellyfin/jellyfin