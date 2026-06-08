# Tópico 03 - Trabalho de Grupo: Publicação de Serviço Web

Este diretório contém o planeamento técnico, arquitetura e documentação para a publicação de um serviço web seguro em ambiente Linux, desenvolvido para a unidade curricular de **Linux, Segurança e Cloud**.

---

## 👥 Identificação do Grupo
* **Grupo:** Grupo X *(Substituir pelo número do vosso grupo)*
* **Elementos:**
  * **Ruddy** - Administrador de Sistemas (Configuração do Nginx, depuração de sintaxe e permissões)
  * **Elemento 2** - Desenvolvedor Web e Documentador *(Substituir pelo nome real)*
---

## 📋 Resumo do Projeto

* **Serviço Escolhido:** Opção B – Pequeno site institucional com HTML e CSS.
* **Rota Técnica:** Servidor Web Nginx em ambiente Linux.
* **Protocolo e Porta:** HTTP na Porta 80 (com mapeamento técnico estruturado para futura transição para HTTPS via Certbot).

### Justificação da Escolha
A rota do **Nginx** foi selecionada devido à sua alta performance e baixo consumo de memória RAM no processamento de ficheiros estáticos, tornando-o ideal para o cenário de um mini-servidor Linux. A opção por um site estático (HTML/CSS) reduz a superfície de ataque e elimina a sobrecarga de bases de dados e motores PHP num ambiente inicial.

---

## 🛠️ Arquitetura e Tarefas Principais

O fluxo segue o modelo: `Cliente/Navegador -> HTTP -> Porta 80 -> Nginx -> Ficheiros Estáticos`.

### Principais Ações Técnicas Executadas:
1. **Saneamento do Servidor:** Remoção de ficheiros de configuração antigos/fantasmas (`your_domain`) que impediam o arranque do serviço.
2. **Depuração de Sintaxe:** Correção de erros estruturais de chavetas (`{}`) e desativação temporária de diretivas SSL órfãs no ficheiro `/etc/nginx/sites-enabled/Enjoaybles.github.io`.
3. **Validação de Rota:** Execução de testes locais no terminal através de `sudo nginx -t` com sucesso completo.

---

## 📁 Estrutura de Ficheiros do Trabalho

```text
linux-seguranca-cloud/
└── topico-03/
    └── trabalho-grupo/
        ├── grupo-X-publicacao-servico-web-topico-03.pdf  <-- Relatório Final
        ├── README.md                                      <-- Este ficheiro
        └── evidencias/                                    <-- Capturas de ecrã dos testes
```

---

## 📄 Relatório Técnico
O plano detalhado com as tabelas de tarefas técnicas, plano de validação local/externo e a matriz de 5 riscos iniciais mitigados encontra-se no documento oficial:
💾 **[Descarregar o Relatório em PDF](./grupo-X-publicacao-servico-web-topico-03.pdf)** *(Ajustar o nome do ficheiro)*

