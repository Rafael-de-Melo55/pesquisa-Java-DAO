Introdução

O que é o DAO? O DAO ( Data Access object ) é um padrão de projeto para separar a lógica de negócio do acesso aos dados.

Em vez de escrever comandos SQL sem organização ou chamar do banco de dados diretamente para o código principal, o DAO cria uma ponte ( objeto DAO ) que cuida exclusivamente dessa comunicação.

O que são classes DAO?, as classes DAO são responsáveis por pela troca de informações com o SGBD ( sistema gerenciador de banco de dados ) e fornecer operações CRUD e de pesquisas, elas devem ser capazes de buscar dados e transformá-los em objetos ou lista de objetos de acordo com o banco de dados, fazendo uso de listas genéricas, também deverão receber e converter os objetos para instruções em SQL e mandar para o banco de dados.

Por que usar?

Organização: O código fica mais compreensível e fácil de ler.

Manutenção: caso ocorra a troca de banco de dados, você pode apenas alterar as classes DAO.

Reuso: você pode reciclar partes do código para outras áreas do mesmo.

E o que é JDBC ( java database connectivity ) é uma API padrão do java que permite que aplicações se conectem e interajam com o banco de dados como o MySQL, SQL server, 
PostgreSQL e etc.

Na prática, ela funciona como uma camada entre o java e o SQL, traduzindo uma linguagem para a outra para o entendimento e funcionamento, para que essa tradução aconteça é necessário um driver JDBC que atua traduzindo o java para o banco de dados, sendo cada banco de dados possuindo seu próprio driver.

Por que usar? 

Interação com o banco de dados: como o java não sabe interagir com todos os bancos de dados automaticamente, se usa o JDBC para isso.







Ciclo de vida da conexão JDBC:

Carregamento do Driver (Driver Loading):
A aplicação carrega o driver JDBC específico do banco de dados (por exemplo, MySQL, PostgreSQL) na memória.

Abertura da Conexão (Establish Connection):
A aplicação solicita uma conexão ao banco de dados utilizando a classe DriverManager ou um DataSource, passando a URL de conexão, usuário e senha.

Criação de Instruções (Create Statements):
A conexão é utilizada para criar objetos que enviam comandos SQL ao banco, como Statement, PreparedStatement ou CallableStatement.

Execução de Consultas/Atualizações (Execute Queries/Updates):
O SQL é enviado, processado pelo SGBDR (parsing, reescrita, otimização) e executado.

Gerenciamento da Transação (Transaction Management):
Operações de commit (confirmação) ou rollback (reversão) são realizadas para garantir a integridade dos dados, geralmente desativando o modo autoCommit para transações complexas.

Fechamento da Conexão (Close Connection):
Crucial: A conexão deve ser fechada tão logo a transação finalize, liberando recursos do banco de dados.

Segurança

O que é SQL injection?

O SQL injection é um uma técnica de ataque baseada na manipulação de dados do SQL, 
Como a maioria dos fabricantes utiliza o padrão SQL-92 ANSI na escrita do código do SQL, os problemas e as falhas de segurança aqui apresentadas se aplicam a todo ambiente que faz uso desse padrão para troca de informações - o que inclui, por exemplo, servidores Oracle. Nesse artigo foram utilizados servidores da plataforma Microsoft: Internet Information Server, Active Server Pages e Microsoft SQL Server.

O que é e porque funciona ?

O SQL injection é uma técnica de ataque onde o invasor pode inserir ou manipular consultas criadas pela aplicação, que são enviadas diretamente pro banco de dados relacional.

Por que o SQL Injection funciona?

Por que a aplicação aceita dados arbitrários fornecidos pelo usuário (“confia” no texto digitado);
As conexões são feitas no contexto de um usuário com privilégios altos.

Tratamento de exceções: 

O que é e por que encapsular o SQL exception?

Encapsular o SQLException é uma prática de desenvolvimento, comum em Java e JDBC, que é basicamente capturar uma exceção de banco de dados genérica e de baixo nível (SQLException) e envolvê-la em uma exceção personalizada, mais específica ou de mais um nível mais alto

Por que fazer isso?

Limpeza do código:
 essa prática evita que as classes de negócio ou serviços tenham que praticar exceções.

Segurança e manutenção: 
 	Evita que detalhes da estrutura do banco de dados sejam expostos ao usuário final ou para camadas superiores da aplicação.

A fundo em conceitos de DAO e JDBC:

O que é ConnectionFactory?

Para não ocorrer a repetição de códigos de abertura de conexão em todas as classes DAO, se utiliza o padrão ConnectionFactory. Ele centraliza a criação de conexões em um único lugar, facilitando a manutenção (como trocar a senha ou a URL do banco) e permitindo o uso de Pool de Conexões para melhorar a performance.

O que é ResultSet mapping?

O banco de dados retorna os dados em formato de tabelas, enquanto isso, o Java trabalha com objetos, o ResultSet Mapping é o processo de percorrer as linhas retornadas pelo banco e transformar esses dados em instâncias das classes do seu sistema.

O que o tratamento de exceções ( exceptions )?

As operações em banco de dados são sensíveis e podem acabar falhando por diversos motivos, como por exemplo, em redes, permissões ou erro de sintaxe. No JDBC, essas falhas geram uma SQLException. É fundamental tratar essas exceções com blocos try-catch para que o sistema possa informar o erro adequadamente em vez de travar por completo.

Como lidar com as transações?

Uma transação garante que um conjunto de operações SQL seja executado como uma unidade única. Seguindo o conceito ACID, as transações asseguram que, se uma parte de um processo complexo falhar, todas as alterações anteriores sejam desfeitas (Rollback). Caso tudo ocorra com sucesso, as alterações são confirmadas definitivamente (Commit).

DAO
https://www.devmedia.com.br/dao-pattern-persistencia-de-dados-utilizando-o-padrao-dao/30999

JDBC
https://medium.com/@gtbarbosa/java-jdbc-hibernate-e-spring-data-jpa-jpa-hibernate-e-jdbc-falando-sobre-java-e-acesso-a-849c8855905e

SQL injection
https://www.devmedia.com.br/sql-injection/6102?utm_dev=google_ads_pmax&gad_source=1&gad_campaignid=22326280955&gclid=Cj0KCQjw2MbPBhCSARIsAP3jP9xck1-aJelv1-hYP259WwHBlZN2t-DYTzka21sDY1Ft_r7BP39cRHMaAie3EALw_wcB

