##Projeto de Automação NodeJS

Foi utilizado, Ansible para automação, instâncias Linux e AWS service.

O projeto consiste em duas receitas, uma para provisionamento do Jenkins e outra para provisionamento da instância que vai deve rodar a aplicação.

A primeira receita, provision_instance.yaml, provisiona uma instância para o serviço nodejs, com um SecurityGroup próprio chamado webserver, e adiciona o IP no arquivo "hosts" para poder executar a task de instalação e configuração da aplicação. A task que é feito o include, webserver.yaml, executa a configuração da aplicação, instala os aplicativos que são necessários, faz o clone do repositório e então executa o NPM INSTALL e START, para que a aplicação suba respondendo na porta 8080. 

Na segunda, provision_jenkins.yaml, é feito a criação da instância do Jenkins com criação de SecurityGroup, adiciona o hosto no arquivo "hosts" para poder executar a seguinte task, tudo em ambiente AWS. Após o provisionamento da instaância, a própria receita aciona a receita jenkins.yaml pelo módulo "include". A receita segue os passos da documentação do Jenkins(https://jenkins.io/doc/book/installing/), após a execução da receita, o IP do host é apresentado e pode ser acessado utilizando a porta 8080. Esse Jenkins foi criado caso seja necessário maior agilidade ou para buildar alguma aplicação, nesse caso não foi necessário a utilização.
