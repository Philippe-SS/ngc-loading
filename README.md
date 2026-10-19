# ngc-loading

Tela de carregamento do servidor nGc.BR Zombie Escape (Garry's Mod), no mesmo visual dos menus do jogo.

- Publicada pelo GitHub Pages em `https://philippe-ss.github.io/ngc-loading/`.
- No servidor: `sv_loadingurl "https://philippe-ss.github.io/ngc-loading/?map=%m&sid=%s"`.
- Um painel só (o antigo layout A; os layouts B e C saíram em 2026-10-19), desenhado para 1920x1080 e escalado para caber na tela.
  `?demo=1` simula o carregamento para ver no navegador.
- Dicas em `TIPS` dentro do `index.html` (etiqueta humano, zumbi ou geral). Regra do dono: só o que o jogador faz, nunca como o jogo
  funciona por dentro nem quem liga o quê.
- Bloco "Novidades" lido de `news.json` (os quatro primeiros itens, `title` e `text`). Sem o arquivo, o bloco some.
- O GMod chama `GameDetails`, `SetStatusChanged`, `SetFilesTotal`, `SetFilesNeeded` e `DownloadingFile`; tudo em `index.html`.
- Bloco "Equipe" (donos, admins e staffs, com avatar e cargo nas cores do jogo) lido de `staff.json`. Sem o arquivo, ou com a
  lista vazia, o bloco some.
- Fotos dos mapas em `maps/<mapa>.jpg` (1280x720, tiradas pelo dono no jogo; `tools/maps/scenic.sh` do nGc.BR faz rascunhos no laboratório; registrar o nome na lista `MAP_PICS`). Fontes Chakra Petch e IBM Plex Sans (licença OFL em `fonts/`).

## Atualizar a equipe

A página é estática e não consegue perguntar ao servidor quem é staff, então a lista fica em `staff.json`, gerado pelo script
`tools/staff.js` do repositório nGc.BR (esta pasta precisa estar ao lado dele, como `GMOD-SERVER/ngc-loading`).

Quando alguém entrar, sair ou mudar de cargo no ULX, rode na pasta do nGc.BR (Git Bash):

```bash
MSYS_NO_PATHCONV=1 node tools/staff.js --push
```

O script lê os grupos do ULX no servidor pelo SFTP (só lê, não muda nada lá), pega nome e foto do perfil público da Steam de cada
um, grava o `staff.json` aqui e faz commit e push. A página publicada mostra a lista nova em cerca de um minuto. Sem `--push` ele
só grava o arquivo; com `--dry` só mostra a lista na tela.

- Quem entra: grupo `superadmin` (Dono), `admin` (Admin) e `staff` (Staff; os nomes antigos `moderator` e `mod` também contam).
  VIP e jogador ficam de fora.
- Ordem: Dono, Admin, Staff; dentro de cada cargo, por nome. No layout A cada cargo começa numa linha.
- Nome e foto são os da Steam no momento em que o script rodou. Se alguém trocar de nome ou de foto, rodar de novo atualiza.
