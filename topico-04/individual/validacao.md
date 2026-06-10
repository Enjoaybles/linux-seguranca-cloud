# Validação de Continuidade do Serviço

## 1. Teste de Acessibilidade Local
Após a ativação da firewall e a reconfiguração do Nginx, executou-se localmente o utilitário de validação:
* **Comando**: `curl -I http://localhost`
* **Resultado**: HTTP/1.1 200 OK (Confirmando que o motor interno do Nginx está operacional).

## 2. Teste de Acessibilidade Externa
* Ligação efetuada a partir de um browser externo apontando para o endereço IP público da máquina.
* **Resultado**: O site HTML renderizou corretamente com todos os estilos CSS associados.

## 3. Validação de Bloqueios de Rede
* Tentativas de conexão externa direcionadas a portos não autorizados (ex: varrimento de portos comuns) falham por *timeout*, comprovando que as regras ativas de bloqueio do UFW estão a descartar pacotes não autorizados com sucesso.
