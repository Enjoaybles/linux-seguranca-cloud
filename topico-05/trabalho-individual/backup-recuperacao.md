# Processo de Cópia de Segurança e Restauro

## 1. Identificação do Diretório Crítico
*   **Alvo do Backup:** `/var/www/html` (Diretório padrão da página de boas-vindas e ficheiros do Nginx).

## 2. Criação do Backup
**Comando executado:**
```bash
sudo tar -czvf /home/ubuntu/backup_nginx_\$(date +%F).tar.gz /var/www/html
```
*   **Resultado:** Ficheiro comprimido `.tar.gz` gerado com sucesso na diretoria home do utilizador, incluindo a marca temporal do dia.

## 3. Restauro na Pasta de Teste
**Comando executado:**
```bash
mkdir -p /home/ubuntu/teste_recuperacao
tar -xzvf /home/ubuntu/backup_nginx_*.tar.gz -C /home/ubuntu/teste_recuperacao
```
## Evidência de Teste e Recuperação
*   **Comando de extração:** `tar -xzvf /home/ubuntu/backup_nginx_*.tar.gz -C /home/ubuntu/teste_recuperacao`
*   **Validação visual:** O conteúdo foi extraído com sucesso, preservando a estrutura `/var/www/html` dentro do diretório de testes.
*   **Ficheiro de imagem:** `evidencias/print_recuperacao_validacao.png`


## 4. Confirmação dos Ficheiros Recuperados
**Comando executado:** `ls -la /home/ubuntu/teste_recuperacao/var/www/html`
*   **Resultado:** Os ficheiros (incluindo o `index.nginx-debian.html`) foram extraídos na pasta de simulação mantendo as permissões de leitura corretas.
