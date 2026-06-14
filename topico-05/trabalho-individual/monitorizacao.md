# Relatório de Monitorização de Recursos (Ubuntu 26.04)

## 1. Tempo de Atividade (Uptime)
**Comando utilizado:** `uptime`
*   **Análise:** Sistema estável. O *load average* demonstra que o consumo de CPU está abaixo do limite crítico do hardware da Máquina Virtual.

## 2. Consumo de Memória RAM
**Comando utilizado:** `free -h`
*   **Análise:** Leitura da memória disponível e em cache. O Ubuntu 26.04 faz uma gestão eficiente de buffers, mantendo o Nginx sem pressões de paginação (Swap).

## 3. Armazenamento em Disco
**Comando utilizado:** `df -h`
*   **Análise:** Verificação efetuada na partição raiz (`/`). Existe espaço suficiente para o crescimento dos ficheiros do Nginx e rotação de logs.

## 4. Estado do Serviço Web
**Comando utilizado:** `sudo systemctl status nginx`
*   **Análise:** O Nginx encontra-se **active (running)**. O processo principal (master process) e os processos trabalhadores (worker processes) estão operacionais.
