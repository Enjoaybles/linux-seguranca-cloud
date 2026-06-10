# Configuração da Firewall (UFW)

## 1. Estado Inicial
Antes da intervenção, o comando `sudo ufw status` indicava `Status: inactive`. O servidor confiava exclusivamente na ausência de serviços secundários para se proteger.

## 2. Estratégia de Filtragem Aplicada
Adotou-se a política de **Lista Branca (Whitelisting)**: bloqueia-se toda a periferia e criam-se exceções pontuais apenas para os portos validados na análise da superfície de ataque.

## 3. Regras Ativas Pós-Configuração
A saída do comando `sudo ufw status verbose` apresenta a seguinte matriz de proteção:

| Porta | Protocolo | Ação | Origem | Justificação |
| :--- | :---: | :--- | :--- | :--- |
| **22** | TCP | ALLOW | Anywhere | Permite acesso SSH para administração remota. |
| **80** | TCP | ALLOW | Anywhere | Permite tráfego Web convencional para leitura do HTML. |
| Anywhere | Qualquer | DENY | Anywhere | Bloqueia qualquer outro porto de entrada por omissão. |
