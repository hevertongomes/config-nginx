### Configuração nginx 

##### Usar usuário admin

1. Instalar o nginx em sua maquina
2. Apois instalar acessar a pasta: cd /etc/nginx/sites-available
2. Criar um arquivo nesse diretório exemplo: fileprovider.conf
3. Dentro desse arquivo adicionar seguinte código de configuração e salvar:

```
server {

    listen       8001; 

    # download
    autoindex on;               # enable directory listing output
    autoindex_exact_size off;   # output file sizes rounded to kilobytes, megabytes, and gigabytes
    autoindex_localtime on;     # output local times in the directory

    location / {
	  root /home/elfo/Documentos/ProjetoSkywalker/recorder-app/recorderapp-backend/recorderapp/gravacoes;
      # Este caminho é onde encontra suas gravações no computador (Deixa ultimo diretório sem barra no final)
    }
}

```

4. Agora é necessário criar um link símbolico para a pasta /etc/nginx/sites-enabled usando o seguinte comando:

```
ln -s /etc/nginx/sites-available/fileprovider.conf /etc/nginx/sites-enabled/fileprovider
```

5. é indicado apagar o arquivo default da pasta /etc/nginx/sites-enabled/

6. Reiniciar o servidor nginx com: systemctl reload nginx.service

7. Verificar se deu tudo certo com: nginx -t

8. Acessar: http://localhost:8001/
