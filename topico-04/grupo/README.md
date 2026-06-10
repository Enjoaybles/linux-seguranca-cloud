# Trabalho Prático: Plano de Segurança Inicial e Hardening

## 👥 Constituição do Grupo
* *Ruddy*
* *Tamiris*
* *Wilson*

## 📂 Estrutura do Tópico 04
A organização deste diretório segue rigorosamente a estrutura metodológica solicitada:

* 📄 grupo-ruddy-tamiris-wilson-seguranca-hardening-topico-04.pdf -> Relatório técnico final detalhado (2 a 4 páginas).
* 📄 README.md -> Este documento de apresentação e enquadramento.
* 📁 evidencias/ -> Pasta destinada aos prints de ecrã e ficheiros de configuração (ex: nginx.conf, regras do ufw).

## ⚙️ Cenário Selecionado
* *Cenário A*: Página HTML com Nginx (Ambiente Linux - Ubuntu Server).

## 🚀 Resumo das Medidas Implementadas
1. *Minimização de Serviços*: Ausência total de base de dados e PHP, reduzindo drasticamente os vetores de ataque.
2. *Segurança de Rede*: Firewall UFW ativa em modo Default Deny Input, libertando apenas as portas 80, 443 e SSH restrito.
3. *Ofuscação de Informação*: Desativação das assinaturas de versão do Nginx (server_tokens off).
4. *Integridade de Ficheiros*: Permissões rigorosas no sistema Linux para o diretório /var/www/html/ (Acesso de escrita bloqueado ao servidor web).
5. *Cifragem de Tráfego*: Configuração de TLS 1.2/1.3 para HTTPS e desativação da listagem de ficheiros (autoindex off).
