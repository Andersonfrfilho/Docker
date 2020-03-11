# Docker
//comando que identifica variavel de ambiente e inicializa as variaveis de ambriente docker
docker
//comando para baixar se nescessario a imagem para realizar um container e inicializa-lo
run
//comando que identifica a imagem que esta sendo executada com o docker no caso o ubuntu
//as imagens vem do repositório oficial do docker o docker hub
ubuntu
//comando que acessa a pasta bin/echo e inicializa o comando echo
/bin/echo
//comando que sera impresso com o comando "Hello Docker!"
docker run ubuntu /bin/echo "Hello Docker!"
//comando para listar as images do docker
docker images
//comando para lista container rodando
docker ps
//comando para listar todos os container mesmo os que não estão rodando
docker ps -a
//comando para criar nome do container
docker run --name database
//comando para setar um valor de variavel de ambiente -e NOME_VARIAVEL_DE_AMBIENTE
docker run --name database -e MYSQL_ROOT_PASSWORD=102030
//comando para rodar o container em segundo plano -d
docker run --name database -e MYSQL_ROOT_PASSWORD=102030 -d
//comando para escolher a imagem que sera instalada ao container NOME_DA_IMAGEM
docker run --name database -e MYSQL_ROOT_PASSWORD=102030 -d mysql
//////////////////////////////////////////////////////////////////////////////////////
//comando --link é para estabelecer uma conexão entre o containers do banco de dados com o container do blog-alura
//onde iremos colocar o nome do container:nomequevcquiser <- tipo um alias
docker run --name blog-alura --link database:mysql
//comando para montar container em uma porta especifica -p 80:80 <- primeiroPortaLocal:portaContainer
docker run --name blog-alura --link database:mysql -e WORLDPRESS_DB_PASSWORD=102030 -p 80:80 -d wordpress
//para entrar em um container em execução exec e como parametro -i interação e o -t para simular o tyx que simula interação com shell 
docker exec -i -t 
//nomedo container e o que quer executar
docker exec -i -t blog-alura
//nome da aplicação que vc quer executar no caso o bash do shell
docker exec -i -t blog-alura bash
//´para sair da um exit 
docker exit
//para entrar em um container docker sem o exec
docker run -i -t ubuntu bash
//forma reduzida
docker run -it ubuntu bash
//apagar container rm id_container||name_container
docker rm nome_container
//apagar todos containers de uma vez using powershell
docker rm ${docker ps -aq)
//apagar imagens 
docker rmi nome_imagem
//startar container
docker start tab+tab -> ajuda a encontrar os nomes
////////////////////////////////////////////////////////
//criar images docker
docker run -it ubuntu bash
//instale o que precisa no container e commit agora saia do container
docker commit -m "instalacao container" id_container ou nome_container 
//nome da imagem
docker commit -m "criando_uma_image" id_container ubuntu/apache
//DockerFile
///////////////////////////////////////////////////////////////
//imagem da instalacao
FROM ubuntu

//instrução para executar apache
RUN apt-get update && apt-get isntall -y apache2
//liberar a porta
EXPOSE 80
//faz o comando que rodara 
CMD ["/usr/bin/apachectl","-D","FOREGROUND"]
docker commit -m "instalacao container" id_container ou nome_container ubuntu/apache
///////////////////////////////////////////////////////////////////
gerar images através do docker files
docker build -t ubuntu/apache 


