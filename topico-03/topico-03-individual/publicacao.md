# Relatório de Publicação Web - Rota A (Nginx)

## 1. Rota Escolhida e Justificação
Foi selecionada a **Rota A – Nginx** para o **Nível 2 (Intermédio)**. A escolha baseia-se na eficiência do Nginx em processar conteúdo estático de forma rápida e com baixo consumo de memória RAM, sendo o padrão de mercado para arquiteturas Cloud modernas.

## 2. Configuração do Servidor
O site foi alojado na diretoria `/var/www/ecotech`. 
A configuração do bloco de servidor (`/etc/nginx/sites-available/ecotech`) foi definida da seguinte forma:

```nginx
server {
    listen 80;
    server_name localhost;

    root /var/www/ecotech;
    index index.html;

    location / {
        try_files uri uri/ =404;
    }
}
```

## 3. Dificuldades Encontradas
- **Gestão de Permissões:** Inicialmente o Nginx devolveu um erro `403 Forbidden`. O problema foi resolvido ajustando as permissões da pasta `/var/www/ecotech` com o comando `chmod 755`.
