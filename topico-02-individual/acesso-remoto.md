# Acesso remoto por SSH

## Estado do servi;o SSH
● ssh.service - OpenBSD Secure Shell server
     Loaded: loaded (/usr/lib/systemd/system/ssh.service; enabled; preset: enabl>
     Active: active (running) since Tue 2026-06-02 16:43:04 UTC; 3h 22min ago
 Invocation: 31a7020d76384600b0a4c2859fce0a85
TriggeredBy: ● ssh.socket
       Docs: man:sshd(8)
             man:sshd_config(5)
    Process: 2145 ExecStartPre=/usr/sbin/sshd -t (code=exited, status=0/SUCCESS)
   Main PID: 2159 (sshd)
      Tasks: 1 (limit: 6198)
     Memory: 1.6M (peak: 2.1M)
        CPU: 36ms
     CGroup: /system.slice/ssh.service
             └─2159 "sshd: /usr/sbin/sshd -D [listener] 0 of 10-100 startups"

Jun 02 16:43:03 Digital systemd[1]: Starting ssh.service - OpenBSD Secure Shell >
Jun 02 16:43:04 Digital sshd[2159]: Server listening on 0.0.0.0 port 22.
Jun 02 16:43:04 Digital sshd[2159]: Server listening on :: port 22.
Jun 02 16:43:04 Digital systemd[1]: Started ssh.service - OpenBSD Secure Shell s>

## Endereco identificado
hostname -I

10.0.***.5** fd1:2:a00:27ff:fe46:cdc1 

## Comando de ligacao
ssh ruddy@10.0.**.**

## Resultado obtido
Welcome to Ubuntu 26.04 LTS (GNU/Linux 7.0.0-22-generic x86_64)

 * Documentation:  https://docs.ubuntu.com
 * Management:     https://landscape.canonical.com
 * Support:        https://ubuntu.com/pro

 System information as of Tue Jun  2 08:14:24 PM UTC 2026

  System load:             0.22
  Usage of /:              37.3% of 24.44GB
  Memory usage:            32%
  Swap usage:              0%
  Processes:               203
  Users logged in:         0
  IPv4 address for enp0s3: 10.0.***.***
  IPv6 address for enp0s3: fd17:****:f02:a00:27ff:fe46:cdc1

 * Strictly confined Kubernetes makes edge and IoT secure. Learn how MicroK8s
   just raised the bar for easy, resilient and secure K8s cluster deployment.

   https://ubuntu.com/engage/secure-kubernetes-at-the-edge

Expanded Security Maintenance for Applications is not enabled.

0 updates can be applied immediately.

1 additional security update can be applied with ESM Apps.
Learn more about enabling ESM Apps service at https://ubuntu.com/esm


Last login: Tue Jun  2 10:49:20 2026 from 192.168.1.97


## Limitacoes encontradas
Aprender novos comandos e saber a extencao da sua utilizacao.

# Acesso remoto e chaves SSH

## Diferenca entre autenticacao por palavra-passe e autenticaca0 por chave
A autenticacao por palavra-passe usa um segredo que o utilizador escreve para provar quem e. 
E simples de usar, mas pode ser menos segura, sobretudo se a palavra-passe for fraca ou se houver tentativas de adivinhacao.

A autenticacao por chave usa um par de chave, normalmente em SSH: a chave privada fica no teu computador e publica fica no servidor.
Em vez de enviares uma palavra-passe, o sistema verifica se tens a chave privada correta.

Em geral, a autenticacao por chave e mais segura e costuma ser mas pratica para acessos remotos frequentes, mas exige configuracao inicial.

## Chave publica
Uma chave publica SSH e a parte publica de um par de chaves usados para autenticacao segura em ligacoes SSH
Ela serve para identificar a tua maquina/utente num servidor remoto.
O servidor usa a chave publica para verificar que quem esta a ligar tem a chave privada correspondente.

Exemplo : ssh-ed25519 AAAAC3NzaC1lDINTE5AAAAIB... teu_email@example.com

Serve para entrar num servidor sem password, automatizar acessos seguros, aumentar a seguranca em comparacao com passwords

## Chave privada
Uma chave privada no Linux e o ficheiro secreto de um de chaves criptograficas, usado para provar a tua identidade.
No SSH, ela corresponde a tua chave publica no servidor.
Nunca deve ser partilhada, copiada para outras pessoas ou enviada por email.
O servidor desafia o cliente, o servidor confirma com a chave publica que es mesmo tu.

## Cuidados de seguranca
- Atualizar o sistema regularmente;
- Usar utilizadores normais, evitando root;
- Ativar firewall;
- Instalar so o necessario;
- Fazer backups;
- Monitorizar logs e recursos;
- Manter boas permissoes nos ficheiros;

## Evidencia segura
