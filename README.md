# docker-protheus-2410
Protheus 2410

<h2>Protheus 12.1.2410  - Postgres </h2>

Procedimentos:
1. Instalar o <b>Docker</b> ( https://www.docker.com/products/docker-desktop/ ). <b>IMPORTANTE:</b> Se voc� possui um Mac com chip M1/M2, desabilite no Docker a op��o "Use Rosetta for x86_64/amd64 emulation on Apple Silicon", caso contr�rio os conteiners podem n�o subir. 
2. Criar uma pasta e copiar os arquivos <b>docker-compose.yml</b> ( https://github.com/emebatista/docker-protheus-2410/blob/main/docker-compose.yml )  e <b>conf.inf</b> ( https://github.com/emebatista/docker-protheus-2410/blob/main/conf.inf )
3. Abrir o terminal dentro da pasta criada e que contém os dois arquivos anteriores e dar os comandos: <br>
```docker login``` <br>
e depois <br>
```docker-compose up -d ``` <br> Se as imagens já estiverem em cache e quiser forçar baixá-las de novo, o comando é <br> ```docker-compose up -d --pull```<br>
No Docker Desktop, o nome do grupo de conteiners será o mesmo do nome da pasta onde foi dado o comando.
4. Acessar o <b>Protheus</b> através do smartclient através na porta <b>1234</b>. O nome do ambiente é <b>P2410</b>. Após subida dos containeres, aguarde 5 minutos até entrar pela primeira vez no sistema, pois logo na primeira construção do container o banco de dados será criado e restaurado o backup inicial. 
5. Acessar o <b>Protheus WebApp</b> através do navegador do endereço <b>http://localhost:4321</b>.
6. Usuário: Admin , senha: msadm
7. O SmartView já vem instalado e pré-configurado em uma máquina virtual chamada smartview-2410 com as portas 7017 e 7019 expostas:
    - Para verificar o status do serviço do SmartView: http://localhost:7019/diagnostic
    - Para alterar configuração do SmartView, criação de conectores, consultas específicas e relatórios, o endereço é http://localhost:7017/
    - Para reconfigurar o SmartView: http://localhost:7019/startup
    - Dentro do Protheus, para poder acessar os relatórios no novo formato, é preciso acessar SIGACFG / Ambiente / Cadastros / Configuração SmartView. Depois escolher a opção "token protheus". É IMPORTANTE informar na url o IP real da máquina (não localhost nem 127.0.0.1), informe no formato http://ip:7017 e clicar 'Testar Conexão'. Exemplo: http://192.168.0.10:7017.
    - Para acessar o WebMonitor: http://localhost:1234/webmonitor
    
Notas:
1) Para utilizar o Protheus na interface sem a porta multiprotocolo, utilize o ambiente P2410D. Esta opção é útil quando se precisa compilar customizações desenvolvidas em ADVPL/TLPP.
2) Para apagar todas as imagens, volumes e containers que não estão rodando, o comando para apagar tudo e manter apenas os volumes do banco de dados e a pasta system_temp, o comando é :<br> ```docker system prune --all --volumes --force``` 
3) Para atualizar e baixar novamente apenas um dos containers, use os comandos<br>
```docker-compose up -d --no-deps --force-recreate license```<br>
```docker-compose up -d --no-deps --force-recreate protheus```<br>
```docker-compose up -d --no-deps --force-recreate db```<br>
```docker-compose up -d --no-deps --force-recreate smartview```<br>
```docker-compose up -d --no-deps --force-recreate dbaccess```<br>