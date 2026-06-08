# Validação do Serviço Web

## 1. Validação Local (Terminal)
O acesso foi testado diretamente no servidor via CLI utilizando o comando `curl`:

```bash
curl -I http://localhost
```

**Resultado esperado no terminal:**
`HTTP/1.1 200 OK`

## 2. Evidências Visuais
*Nota: Deves tirar prints do teu ecrã e guardá-los na pasta `evidencias/`.*

- **Estado do Serviço:** `![Status do Nginx](evidencias/status_nginx.png)` (Print do comando `systemctl status nginx` ativo).
- **Página Inicial:** `![Página Index](evidencias/print_index.png)` (Print do browser a aceder ao site).
- **Página Sobre:** `![Página Sobre](evidencias/print_sobre.png)` (Print do browser na página sobre.html).
