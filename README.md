# Avaliação Sprint 1
### _Criando um container com docker rodando express!_
 ---
## Por que Docker?
 
- **Segurança**, o docker cria um ambiente sem interferências externas.
- **Organização**, já que pode-se dividir vários serviços entre containers diferentes.
- **Performance**, rodar uma imagem docker é bem mais leve que rodar uma máquina virtual.
- **Replicação**, pois é muito simples compartilhar imagens com outras pessoas.
 
## Como o projeto se relaciona com os estudos feitos?
Cursos feitos:
- Gestão Ágil com Scrum COMPLETO
- Métodos ágeis de A a Z
- Segurança em Aplicações WEB
- Git Completo: Do Básico ao Avançado
- JavaScript do básico ao avançado

>Primeiramente é importante ressaltar que o conhecimento de **Scrum e metodologias Ágeis** foi um grande facilitador no 
processo de estudo. As dailys e a auto-organização me deram mais objetivo e controle, sobre o que eu deveria estudar e fazer.
Então esse projeto só pode ser feito graças a toda metodologia que aprendi nos cursos de _agile_.
 
>Em seguida vêm o de **Javascript**, mesmo que com conhecimento prévio sempre é importante revisar os conteúdos para o constante aprimoramento!
e sem esse conhecimento seria difícil compreender por exemplo o código do express, ou como o node funciona.
 
>O de **Docker** também foi imprescindível, já que é uma core feature do projeto. 
Com o Docker é possível o encapsulamento do código, que é executado em um container.
Só assim eu posso ter certeza que o código funcionará em qualquer outro lugar!
 
>E por último o de **Git!** que possibilitou que eu e meus colegas possamos compartilhar essa avaliação.
Além disso ele provê um ambiente completo de desenvolvimento, podendo também fazer o 
versionamento, compartilhar conhecimentos com outras pessoas dispostas a colaborar e muito mais.
 
>Infelizmente não consegui aplicar os conhecimentos de pen-testing aprendidas no curso de **Segurança web.**
Mas com toda certeza agora sou capaz de formular códigos mais seguros!


## Como foi feito?
 
Primeiro foi feito o código do "app.js" (Que está documentado explicando o que cada parte do código faz!)
 
Depois foi necessário criar o package.json, que guarda informações e dependências do projeto, a partir do comando:
```sh
npm init
```
 
E instalar os pacotes a serem usados: express e nodemon.
```sh
npm install --save express
npm install --save nodemon
```
 
Depois criei um novo script para execução do código no package.json, no caso o start, usando o nodemon.
``` json
{"start": "nodemon app.js"}
```
 
E por último foi só configurar o container através do Dockerfile! (Que também está documentado)



## Como executar o código?
 
>  Obs: Antes de tudo tenha certeza de ter o Docker instalado! 
 
Primeiro, baixe o código ou clone o repositório.
 
No diretório do projeto, abra o terminal e  digite:
 
```sh
docker build -t docker-container-nodejs .
```
Esse código gera uma imagem chamada "docker-container-nodejs" baseada no arquivo **Dockerfile** do projeto.
O **-t** define o nome da imagem, e o **.** define o diretório que o código se encontra (nesse caso o diretório local)
 
Em seguida o seguinte comando:
```sh
docker run -d -p 8000:3000 -v node-app-volume:/data docker-container-nodejs
```
Aqui o Docker gera um container baseado na imagem criada e o ínicia logo em seguida.
O **-d** vem de _detached_, e serve para separar o processo do terminal.
O **-p** é o encaminhamento de portas do container, no caso nós acessamos a porta 3000 pela porta 8000.
O **-v** serve para criar um volume ligado ao container, "node-app-volume" é o nome do volume e "data" é o local do volume.
E o "docker-container-nodejs" serve para indicar sobre qual imagem será montada o container.
 
E pronto! agora é só acessar localhost:8000
 