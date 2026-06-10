# Atividade Individual: Segurança e Hardening Inicial (Tópico 04)

## 👤 Identificação do Formando
* **Nome**: [Ruddy Timas]
* **Perfil do Serviço**: Cenário A – Página HTML estática servida por Nginx em ambiente Linux.

## 📁 Organização das Entregas
Este diretório cumpre a estrutura modular requerida para a atividade individual:

* 📄 `superficie-ataque.md` -> Mapeamento de portos, serviços e riscos operacionais (Nível 1).
* 📄 `firewall.md` -> Documentação das regras e políticas aplicadas com o UFW (Nível 2).
* 📄 `hardening.md` -> Plano de proteção com o que foi feito no Nginx e o roteiro futuro (Nível 3).
* 📄 `validacao.md` -> Testes de integridade que provam que o serviço web continua online.
* 📄 `comandos.txt` -> Histórico limpo de comandos de consola utilizados na atividade.
* 📁 `evidencias/` -> Repositório de imagens com capturas de ecrã dos outputs do terminal (ex: `ufw status`).

## 🛠️ Resumo Técnico da Intervenção
1. **Rede Blindada**: Ativação do UFW com política restritiva de entrada e liberação estrita dos portos 22 e 80.
2. **Privilégio Mínimo**: Permissões do sistema de ficheiros corrigidas (`644`/`755`) retirando permissão de escrita ao Nginx.
3. **Ofuscação**: Remoção das assinaturas públicas de versão do Nginx para mitigar engenharia reversa e reconhecimento direcionado.
