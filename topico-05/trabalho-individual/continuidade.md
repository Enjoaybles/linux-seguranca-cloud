# Plano de Continuidade Operacional do Servidor Nginx

## 1. Ativos Críticos e Logs
*   **Diretórios:** `/var/www/html` (Conteúdo) e `/etc/nginx/` (Ficheiros de configuração de blocos de servidor/vhosts).
*   **Logs Monitorizados:** `/var/log/nginx/error.log` para falhas e `/var/log/nginx/access.log` para tráfego anómalo.

## 2. Estratégia e Periodicidade de Backup
*   **Configurações do Nginx (`/etc/nginx`):** Backup semanal (as configurações mudam raramente).
*   **Dados Web (`/var/www/html`):** Backup diário automático via rotina Cron às 03:00 AM.

```bash
# Entrada sugerida para o crontab automático (sudo crontab -e)
0 3 * * * tar -czvf /var/backups/nginx_html_\$(date +\%F).tar.gz /var/www/html
```

## 3. Procedimento de Recuperação de Desastre (Disaster Recovery)
1.  Reinstalação do servidor limpo: `sudo apt update && sudo apt install nginx -y`.
2.  Restaurar as configurações guardadas em `/etc/nginx/sites-available/`.
3.  Reativar o site criando o link simbólico: `sudo ln -s /etc/nginx/sites-available/default /etc/nginx/sites-enabled/`.
4.  Extrair o conteúdo web no destino: `sudo tar -xzvf backup_nginx_*.tar.gz -C /`.
5.  Validar a sintaxe do Nginx: `sudo nginx -t`.
6.  Reiniciar o serviço: `sudo systemctl restart nginx`.

## 4. Critérios de Sucesso e Validação
*   O comando `sudo nginx -t` deve retornar `syntax is ok` e `test is successful`.
*   O comando `curl -I http://localhost` deve responder com o código de estado HTTP `200 OK`.
