# ngc-loading

Tela de carregamento do servidor nGc.BR Zombie Escape (Garry's Mod), no mesmo visual dos menus do jogo.

- Publicada pelo GitHub Pages em `https://philippe-ss.github.io/ngc-loading/`.
- No servidor: `sv_loadingurl "https://philippe-ss.github.io/ngc-loading/?map=%m&sid=%s"`.
- `?v=a|b|c` escolhe o layout (propostas em teste); `?demo=1` simula o carregamento para ver no navegador.
- O GMod chama `GameDetails`, `SetStatusChanged`, `SetFilesTotal`, `SetFilesNeeded` e `DownloadingFile`; tudo em `index.html`.
- Fotos dos mapas em `maps/<mapa>.jpg` (1280x720, tiradas pelo dono no jogo; `tools/maps/scenic.sh` do nGc.BR faz rascunhos no laboratório; registrar o nome na lista `MAP_PICS`). Fontes Chakra Petch e IBM Plex Sans (licença OFL em `fonts/`).
