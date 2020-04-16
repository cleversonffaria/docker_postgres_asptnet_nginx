# docker_postgres_asptnet_nginx

## Deletando todos os containers

```bash
docker rm -f $(docker ps -a -q)
```


## Deletando todos os volumes

```bash
docker volume rm $(docker volume ls -q)
```

<strong>PostGres start : </strong>
  - Troque o usuario e a senha do services <strong> postgres</strong>.
  - Troque o emial e senha do services <strong>pgadmin</strong>.
  
  <strong>Aspnet e nginx : </strong>
  - Coloque seu app completo dentro da pasta <strong> APP</strong>.
  - Verifique as versoes do Aspnet, a do seu pc e a imagem no docker tem que ser a mesma.
  - Para baixa as versoes no docker consulte a documentação : https://hub.docker.com/r/microsoft/aspnetcore/.
  - Troque o <strong> NOME_DA_PASTA </strong>e o<strong> NOME_DO_ARQUIVO </strong>para os respectivos no seu projeto.
  
  <strong>Executando dockers : </strong>
  ```bash
  docker-compose up --build     // Para executar realizando uma nova build no projeto usando cache
  docker-compose up             // Para executar o projeto ja buildado
  docker-compose ps             // Para verificar se os componentes estao rodando
  ```
  
  Dentro da pasta APP:
   // Para buildar o projeto
  ```bash
  docker build -t NOME_DA_IMAGEM . 
  ```
  
  // Para executar o bash dentro da imagem do projeto. Comando " ls " para ver as pastas existentes.
  ```bash
  docker run -it -p 5000:5000 --entrypoint /bin/bash NOME_DA_IMAGEM
  ```  
  
   // Para executar a imagem.
 ```bash
  docker run -it NOME_DA_IMAGEM
  ```  

