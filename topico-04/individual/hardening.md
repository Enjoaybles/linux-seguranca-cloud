# Plano de Hardening Inicial: Nginx

## 1. Riscos Específicos do Serviço Aplicado
* Listagem de ficheiros ativa (`autoindex`), permitindo a visualização indesejada da estrutura de pastas.
* Permissões de escrita abusivas no diretório `/var/www/html/` que facilitam a adulteração dos ficheiros estáticos em caso de quebra de outro vetor de isolamento.

## 2. Medidas de Hardening Aplicadas Imediatamente
* **Ocultação de Metadados**: Adicionada a diretiva `server_tokens off;` no ficheiro `/etc/nginx/nginx.conf` para omitir a versão do Nginx nos erros HTTP.
* **Desativação de Indexação**: Configurada a diretiva `autoindex off;` no bloco de servidor do site por omissão.
* **Ajuste de Permissões Unix**: O utilizador do Nginx (`www-data`) foi despromovido a permissões exclusivas de leitura. Ficheiros alterados para `644` e pastas para `755`, com dono atribuído ao utilizador administrativo `root`.

## 3. Medidas Agendadas para Tópicos Seguintes
* **Migração para HTTPS**: Aquisição e renovação automatizada de um certificado TLS via [Let's Encrypt](https://letsencrypt.org).
* **Restrição de Métodos HTTP**: Configurar o Nginx para rejeitar pedidos do tipo `POST`, `PUT` ou `DELETE`, uma vez que a página é estática e aceita apenas `GET` e `HEAD`.
* **Segurança do SSH**: Mudar o porto padrão de 22 para um porto alto aleatório e desativar o login remoto direto do utilizador *root*.
