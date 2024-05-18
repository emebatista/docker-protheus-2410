# docker-protheus-2410
Protheus 2410

<h2>Protheus 12.1.2310  - Postgres </h2>

Procedimentos:
1. Instalar o <b>Docker</b> ( https://www.docker.com/products/docker-desktop/ )
2. Criar uma pasta e copiar os arquivos <b>docker-compose.yml</b> ( https://github.com/emebatista/docker-protheus-2310/blob/main/docker-compose.yml )  e <b>conf.inf</b> ( https://github.com/emebatista/docker-protheus-2310/blob/main/conf.inf )
3. Abrir o terminal dentro da pasta criada e que contém os dois arquivos anteriores e dar o comando: <b>docker-compose up -d </b>. Se as imagens já estiverem em cache e quiser forçar baixá-las de novo, o comando é docker-compose up -d --pull. No Docker Desktop, o nome do grupo de conteiners será o mesmo do nome da pasta onde foi dado o comando.
4. Acessar o <b>Protheus</b> através do smartclient através na porta <b>1234</b>. O nome do ambiente é <b>P2310</b>. Após subida dos containeres, aguarde 5 minutos até entrar pela primeira vez no sistema, pois logo na primeira construção do container o banco de dados será criado e restaurado o backup inicial. 
5. Acessar o <b>Protheus WebApp</b> através do navegador do endereço <b>http://localhost:4321</b>.
6. Usuário: Admin , senha: msadm
7. O SmartView já vem instalado e pré-configurado em uma máquina virtual chamada smartview-2310 com as portas 7017 e 7019 expostas:
    - Para verificar o status do serviço do SmartView: http://localhost:7019/diagnostic
    - Para alterar configuração do SmartView, criação de conectores, consultas específicas e relatórios, o endereço é http://localhost:7017/
    - Para reconfigurar o SmartView: http://localhost:7019/startup
    - Dentro do Protheus, para poder acessar os relatórios no novo formato, é preciso acessar SIGACFG / Ambiente / Cadastros / Configuração SmartView. Depois escolher a opção "token protheus". É IMPORTANTE informar na url o IP real da máquina (não localhost nem 127.0.0.1), informe no formato http://[ip]:7017 e clicar 'Testar Conexão'. 
    
Observação:
Se quiser utilizar o Protheus na interface sem a porta multiprotocolo, utilize o ambiente P2310D. Esta opção é útil quando se precisa compilar customizações desenvolvidas em ADVPL/TLPP.