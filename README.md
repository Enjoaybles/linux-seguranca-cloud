# Relatório do Trabalho de Grupo

## Proposta de Controlo de Acessos para Mini-Servidor Linux

### 1. Síntese do Cenário

Uma pequena equipa pretende implementar um mini-servidor Linux para alojar uma aplicação web. O servidor será utilizado por diferentes perfis de utilizadores, nomeadamente administradores, operadores web, auditores e visitantes técnicos.

Foram identificados vários riscos de segurança, incluindo a utilização da mesma conta por vários utilizadores, permissões excessivas em diretórios, utilização frequente da conta root, acesso remoto sem controlo e falta de documentação sobre responsabilidades.

O objetivo desta proposta é organizar os acessos ao servidor de forma segura, aplicando o princípio do menor privilégio e boas práticas de administração Linux.

### 2. Perfis, Grupos e Responsabilidades

| Perfil                   | Grupo sugerido | Responsabilidades                                       | Permissões necessárias                              | Permissões a evitar              |
| ------------------------ | -------------- | ------------------------------------------------------- | --------------------------------------------------- | -------------------------------- |
| Administrador do sistema | admins         | Gerir utilizadores, permissões, serviços e atualizações | Leitura e escrita em todo o sistema através de sudo | Utilização diária da conta root  |
| Operador Web             | webops         | Publicar e atualizar a aplicação web                    | Leitura e escrita na pasta da aplicação             | Alterar configurações do sistema |
| Auditor                  | auditores      | Consultar logs, documentação e evidências               | Apenas leitura em logs e documentação               | Alterar ou apagar ficheiros      |
| Visitante Técnico        | visitantes     | Consultar documentação autorizada                       | Apenas leitura na documentação pública              | Acesso a configurações e logs    |

#### Justificação

A separação de utilizadores por grupos permite aplicar o princípio do menor privilégio, garantindo que cada utilizador possui apenas os acessos necessários para desempenhar as suas funções.

### 3. Estrutura de Diretórios Proposta

Estrutura sugerida:

/linu-seguranca-cloud/projeto-web/
├── public/
├── config/
├── logs/
└── docs/

#### public/

Contém os ficheiros públicos da aplicação:

* HTML
* CSS
* JavaScript
* imagens

Leitura:

* Administradores
* Operadores Web
* Auditores
* Visitantes

Escrita:

* Administradores
* Operadores Web

#### config/

Contém:

* credenciais
* configurações da aplicação
* configurações da base de dados

Leitura e escrita:

* Apenas administradores

Sem acesso:

* Operadores Web
* Auditores
* Visitantes

#### logs/

Contém:

* logs de acesso
* logs de erro
* registos de auditoria

Leitura:

* Administradores
* Auditores

Escrita:

* Sistema
* Administradores

#### docs/

Contém:

* documentação técnica
* relatórios
* evidências

Leitura:

* Todos os utilizadores

Escrita:

* Administradores
* Auditores

#### Justificação

A separação dos ficheiros públicos, configurações, logs e documentação reduz o risco de acessos indevidos e facilita a administração do servidor.

### 4. Proposta de Permissões

| Caminho             | Dono/Grupo sugerido   | Permissão        | Justificação                             |
| ------------------- | -------------------   | ----------       | --------------------------------------- |
| /projeto-web        | root:admins           | 755              | Estrutura principal do projeto          |
| /projeto-web/public | root:webops           | 775              | Operadores podem atualizar conteúdos    |
| /projeto-web/config | root:admins           | 750              | Proteção de credenciais e configurações |
| /projeto-web/logs   | root:auditores        | 750              | Preservação das evidências de auditoria |
| /projeto-web/docs   | root:auditores        | 775              | Documentação acessível e atualizável    |

#### Justificação

As permissões foram definidas de forma a garantir que cada grupo possui apenas os acessos necessários às suas funções.

### 5. Regras de Acesso Remoto por SSH

| Perfil            | Pode aceder por SSH? | Tipo de autenticação | Justificação                     |
| ----------------- | -------------------- | -------------------- | -------------------------------- |
| Administrador     | Sim                  | Chave SSH            | Necessita gerir o sistema        |
| Operador Web      | Sim                  | Chave SSH            | Necessita atualizar a aplicação  |
| Auditor           | Sim                  | Chave SSH            | Necessita consultar logs         |
| Visitante Técnico | Não                  | Não aplicável        | Não necessita acesso ao servidor |

#### Boas práticas

* Utilizar contas individuais.
* Não utilizar contas partilhadas.
* Utilizar autenticação por chave SSH.
* Desativar login remoto do root.
* Limitar acesso aos grupos autorizados.

#### Informação que nunca deve ser publicada

* Passwords
* Chaves privadas SSH
* Tokens de acesso
* Credenciais da base de dados
* Ficheiros de configuração sensíveis

#### Justificação

A utilização de chaves SSH e contas individuais aumenta a segurança e permite identificar quem realizou cada ação no servidor.

### 6. Riscos e Medidas de Mitigação

| Risco                                             | Impacto                         | Medida de mitigação                     |
| ------------------------------------------------- | ------------------------------- | --------------------------------------- |
| Utilização da mesma conta por vários utilizadores | Falta de rastreabilidade        | Utilizar contas individuais             |
| Utilização frequente da conta root                | Comprometimento do sistema      | Utilizar sudo e desativar login root    |
| Permissões excessivas em diretórios               | Alteração indevida de ficheiros | Aplicar o princípio do menor privilégio |
| Configurações sensíveis acessíveis                | Exposição de credenciais        | Restringir acesso à pasta config        |
| Acesso SSH sem controlo                           | Intrusões e ataques remotos     | Utilizar chaves SSH e limitar acessos   |

#### Justificação

A identificação prévia dos riscos permite implementar medidas preventivas e aumentar a segurança geral do servidor.

### 7. Conclusão

A proposta apresentada organiza os acessos ao mini-servidor Linux de forma segura e estruturada. Foram definidos perfis de utilizadores, grupos, permissões adequadas e regras para acesso remoto por SSH, respeitando o princípio do menor privilégio.

A separação de responsabilidades reduz riscos de alterações indevidas, protege informação sensível e facilita auditorias. A utilização de contas individuais, permissões restritivas e autenticação por chave SSH contribui para aumentar a segurança do servidor e garantir uma administração mais eficiente.

Desta forma, o mini-servidor fica preparado para suportar futuras configurações e serviços ao longo do módulo.
