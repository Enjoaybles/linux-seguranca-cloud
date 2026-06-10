# Caracterização da Superfície de Ataque

## 1. Identificação do Serviço
* **Serviço Web Base**: Servidor Web Nginx (Entrega de conteúdos HTML/CSS estáticos).
* **Sistema Operativo**: Linux (Distribuição baseada em Debian/Ubuntu).

## 2. Portas e Serviços Ativos Detetados
* **Porta 22/TCP**: Serviço `sshd` (OpenSSH Server) ativo para administração remota.
* **Porta 80/TCP**: Serviço `nginx` ativo para atendimento de requisições HTTP públicas.

## 3. Análise de Necessidade de Portas
* **Porta 22 (SSH)**: **Necessária**. Essencial para a gestão, atualização e envio de novos ficheiros HTML pelo administrador.
* **Porta 80 (HTTP)**: **Necessária**. Garante o primeiro ponto de contacto do utilizador comum com o site.
* **Porta 443 (HTTPS)**: **Não configurada**. Deverá ser aberta no futuro quando existir um certificado SSL/TLS ativo.
* **Porta 3306 (MySQL/MariaDB)**: **Desnecessária/Inexistente**. Por ser uma página HTML estática, não há base de dados ativa, eliminando este vetor.

## 4. Identificação de Risos Iniciais
1. **Ataques de Força Bruta no SSH**: A porta 22 exposta à internet global atrai tentativas automatizadas de adivinhação de credenciais.
2. **Exposição de Informação Crítica (Information Disclosure)**: O cabeçalho HTTP padrão do Nginx exibe a versão exata do software, ajudando atacantes a mapear vulnerabilidades conhecidas.
3. **Tráfego em Texto Limpo (HTTP)**: Os dados circulam sem encriptação, permitindo ataques de interceção em redes partilhadas.
