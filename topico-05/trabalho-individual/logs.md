# Análise de Registos de Eventos (Nginx / Ubuntu)

## 1. Consulta de Logs Recentes do Serviço
**Comando utilizado:** `sudo journalctl -u nginx -n 20` ou `sudo tail -n 20 /var/log/nginx/access.log`

## 2. Evento Relevante Identificado
*   **Ficheiro Origem:** `/var/log/nginx/error.log`
*   **Linha do Evento:** `2026/06/14 09:12:01 [notice] 1042#1042: using the "epoll" event method`
*   **Explicação:** Este é um evento de nível *notice* gerado durante o arranque ou recarregamento do Nginx. O sistema informa que está a usar o método `epoll`, que é o mecanismo nativo e de alto desempenho do kernel do Linux para gerir conexões simultâneas. O evento confirma o comportamento ideal do servidor.
