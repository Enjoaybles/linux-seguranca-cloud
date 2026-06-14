# Atividade Individual - Tópico 05: Gestão de Sistemas e Continuidade

Este repositório contém as evidências, relatórios e planos de continuidade operacional desenvolvidos para a gestão de um servidor web **Nginx** focado no sistema operativo **Ubuntu 26.04**.

---

## 📁 Estrutura de Ficheiros

*   `monitorizacao.md`: Relatório do estado atual do hardware (Uptime, CPU, RAM e Disco).
*   `logs.md`: Análise de registos de eventos do Nginx e do sistema através do `journalctl`.
*   `backup-recuperacao.md`: Detalhes sobre o processo de compactação e o teste prático de integridade.
*   `continuidade.md`: Plano estratégico de recuperação de desastres (Disaster Recovery) para o servidor.
*   `comandos.txt`: Histórico limpo de todos os comandos executados no terminal durante a atividade.
*   `evidencias/`: Pasta que armazena as capturas de ecrã (prints) que comprovam as execuções.

---

## 🛠️ Como Executar e Replicar os Testes

### 1. Monitorização Básica (Nível 1)
Para verificar o estado dos recursos do sistema de uma só vez, execute:
```bash
uptime && free -h && df -h && sudo systemctl status nginx
```

### 2. Ciclo de Backup e Restauro (Nível 2)
Para simular a criação do backup e a respetiva recuperação na pasta de testes com verificação de integridade:
```bash
# Criação do backup seguro no diretório do utilizador
sudo tar -czvf /tmp/backup_nginx_\$(date +%F).tar.gz /var/www/html && sudo mv /tmp/backup_nginx_*.tar.gz /home/ubuntu/

# Execução do teste de restauro isolado e listagem de ficheiros
mkdir -p /home/ubuntu/teste_recuperacao && tar -xzvf /home/ubuntu/backup_nginx_*.tar.gz -C /home/ubuntu/teste_recuperacao && ls -la /home/ubuntu/teste_recuperacao/var/www/html
```

---

## 📸 Evidências Visuais Guardadas

As capturas de ecrã que comprovam o sucesso desta atividade encontram-se na diretoria `evidencias/` com a seguinte nomenclatura padrão:
1.  **`print_monitorizacao.png`**: Demonstra o consumo de RAM, espaço em disco e uptime.
2.  **`print_log_evento.png`**: Demonstra a recolha de eventos ativos do serviço Nginx.
3.  **`print_recuperacao_validacao.png`**: Comprova a extração bem-sucedida dos ficheiros de backup na diretoria de testes.
