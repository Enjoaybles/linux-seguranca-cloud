# Plano de Monitorização, Backup e Continuidade Operacional

Este repositório contém o trabalho prático desenvolvido para o **Tópico 05**, focado no desenho e implementação de estratégias de resiliência, acompanhamento técnico e recuperação de desastres para um serviço web publicado.

## 📋 Cenário Escolhido
* **Cenário A**: Serviço Web HTML com Servidor Nginx em Linux (Ubuntu Server).
* **Foco do Trabalho**: Garantir a integridade dos ficheiros estáticos, alta disponibilidade do motor Nginx, mitigação de ataques estruturais e gestão eficiente de armazenamento e logs.

## 📁 Estrutura do Repositório
A organização dos ficheiros segue estritamente os requisitos definidos pelo guião do projeto:

```text
topico-05/
└── trabalho-grupo/
    ├── grupo-7-monitorizacao-continuidade-topico-05.pdf  <-- Relatório Oficial em PDF
    ├── README.md                                         <-- Este ficheiro de apresentação
    └── evidencias/                                       <-- Capturas de ecrã e logs do sistema
```

## 👥 Identificação do Grupo
* **Grupo**: Grupo X *(Substituir pelo número do vosso grupo)*
* **Elementos e Papéis**:
  * **Elemento 1 (Ruddy Timas)**: Administrador de Sistemas (SysAdmin) & Plano de Backup
  * **Elemento 2 (Tamiris Evora)**: Engenheiro de Monitorização (DevOps) & Gestão de Logs
  * **Elemento 3 (Wilson Mendonca)**: Gestor de Continuidade (SecOps) & Plano de Recuperação

## 🚀 Resumo das Componentes Implementadas

1. **Caracterização do Serviço**: Mapeamento dos ficheiros críticos de configuração do Nginx (`nginx.conf`, `default`) e análise dos vetores de risco (como a paragem do binário e *defacement*).
2. **Plano de Monitorização**: Definição de métricas de saúde do sistema (CPU, RAM, Espaço em Disco) com ferramentas de validação nativas (`df`, `free`, `systemctl`).
3. **Plano de Logs**: Estruturação da auditoria de sistema e acessos através dos ficheiros `access.log`, `error.log`, `auth.log` e do utilitário `journalctl`.
4. **Plano de Backup**: Política de salvaguarda semanal incremental para ficheiros estáticos e configurações web, baseada na estratégia de segurança 3-2-1.
5. **Plano de Recuperação**: Guião de procedimentos lineares e simplificados para resolução rápida de falhas comuns (erros HTTP 404/403, disco cheio e quedas de serviço).

## 🛠️ Como replicar a estrutura localmente
Caso necessite de validar a árvore de diretórios localmente no Ubuntu, execute os seguintes comandos:
```bash
git clone https://github.com
cd topico-05/trabalho-grupo/
tree
```

---

