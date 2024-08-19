# Put jellyfin Image
docker pull jellyfin/jellyfin
# Create dir for cache, config and media Volume
mkdir /pathtodir/cache
mkdir /pathtodir/config
mkdir /pathtodir/media
# Or careate volume
docker volume create jellyfin-cache
docker volume create jellyfin-cache
# Run jellyfin container by docker compose
services:
  jellyfin:
    image: jellyfin/jellyfin
    container_name: jellyfin-by-compose
    user: 1000:1000
    volumes:
      - /home/shohel/mygithub/docker-project/docker-project/Jellyfin-Compose/config:/config
      - /home/shohel/mygithub/docker-project/docker-project/Jellyfin-Compose/cache:/cache
      - type: bind
        source: /home/shohel/mygithub/docker-project/docker-project/Jellyfin-Compose/media
        target: /media
        read_only: true
    ports:
      - 8091:8096/tcp
    restart: 'unless-stopped'
