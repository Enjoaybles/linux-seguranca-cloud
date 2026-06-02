# Permissoes aplicadas

## Ambiente utilizado
VM Local no Ubuntu 25.04 LTS, DE -- KDE Plamas 6.6

## Utilizador e grupos
 - whoami : ruddy
 - id : uid=1000(ruddy) gid=1000(ruddy) groups=1000(ruddy),4(adm),24(cdrom),27(sudo),30(dip),46(plugdev),100(users),101(lxd),983(vboxsf) 
 - groups : ruddy adm cdrom sudo dip plugdev users lxd vboxsf

## Ficheiros criados
 - publico.txt : 
 - restrito.txt :
 - script.sh :

## Permissoes aplicadas
Ficheiro     |   Permissao   | Justificacao

publico.txt  |     644       | Permissao de leitura e escrita para o dono, leitura para outros.
restrito.txt |     640       | Permissao de leitura e escrita para o dono, leitura para o grupo.
script.sh    |     u+x       | Permitir execucao do script apenas para o dono.

## Relacao com o principio do menos privilegio
As permissoes aplicadas garantem que cada arquivo so pode ser acessado por utilizadores que realmente necessitam, evitando acessos nao autorizados e aumentando a seguraca.
