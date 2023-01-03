A Raspberry Pi4 4gb based NAS using OMV6 and Docker, that I also call ShortCrust.

The number of containers now running on this has occasionally led to some major slow downs and website freezing. Because of this and as I have a number of computer spare parts now, i think i'll just update the entire infrastructure of this project [[PuffCrust]]. As an intermediary step I have added a portainer agent (A Raspberry Pi 4 called Docker-1, D1) to expand the docker capabilities of the Vault, this is now effectively a 1x head and 1x node cluster.

## Hardware
| Hardware | Description |
|---|---|
|2 x Raspberry Pi 4 | 4Gb + 32Gb SD card |
| External HDD | 4Tb |
| External HDD | 10 Tb |

## Services
| Service | Port | Description | Site |
|---|---|---| --- |
| Open Media Vault 6 | 10.0.0.2 | The NAS operating system | [OMV](https://www.openmediavault.org/)
| Homepage | D1:3100 | A Homepage to collect all services | [Homepage GH](https://github.com/benphelps/homepage)
| Portainer | :9000 | Docker manager | [Portainer](https://www.portainer.io/)
| Plex | :32400 | Media viewer | [Plex Docker](https://github.com/linuxserver/docker-plex)
| Jellyfin | :8096 | Media viewer (FOSS alt to Plex) | [Jellyfin Docs]() 
| Tautulli | :8181 | Plex Stat Tracker | [Tautulli Docker](https://hub.docker.com/r/tautulli/tautulli)
| Airsonic |  :4040 | Local Music Player | [Airsonic](https://hub.docker.com/r/linuxserver/advanced-airsonic)
| Kavita | :5000 | Comic and Book Viewer | [Kavita Wiki](https://wiki.kavitareader.com/en)
| meTube | :9090 | Video Download Server | [MeTube GH](https://github.com/alexta69/metube)
| Ubuntu | :1234 | Dev environment | [Ubuntu Docker](https://hub.docker.com/_/ubuntu)
| Nginx Proxy Manager | D1:86 | Proxy Manager | NPM |
| Obsidian-remote | D1:NPM:8900 | Home accessible Obsidian Instance | [obs-remote](https://github.com/sytone/obsidian-remote)



