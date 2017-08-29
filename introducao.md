# Conceitos

A linguagem **SQL** *(**S**tructured  **Q**uery **L**anguage)* que em livre tradução do inglês quer dizer *linguagem de consulta estruturada* foi concebida e desenvolvida pela *IBM[^1]* a partir dos conceitos de *E. F. Codd*, publicados em sua pesquisa[^2], em 1970.

Muito mudou nestes 47 anos dos **SGBDR**[^3] *- **S**istema **G**erenciados de **B**anco de **D**ados **R**elacional -* e isso pode ser verificado a partir do trabalho de duas entidades de padronização: *ANSI* e *ISO*. a SQL começa a ser padronizado pela ANSI em 1996 e as duas entidades seguem até hoje normatizando a linguagem. O padrão SQL mais recente, de nível completo está dividido em 15 partes que podem ser adquiridas separadamente no site da ISO[^4].

Conforme Oliveira[^5] nos ensina a "SQL é um conjunto de comandos de manipulação de banco de dados utilizado para criar e manter a estrutura desse banco de dados, além de incluir, excluir, modificar e pesquisar informações nas tabelas dele".

*Toby [et al, 265]*[^6], afirma que a SQL é fundamental para os **SGBDR**. Assim, ele apresenta um descolamento da linguagem de sua principal ferramenta e reforça essa evidência quando escreve que "a *SQL* é uma linguagem de definição e manipulação de dados padrão *ISO-ANSI* para sistemas de gerenciamento de banco de dados relacionais. Os sistemas de banco de dados relacionais individuais utilizam variações da sintaxe SQL e regras de nomeação ligeiramente diferentes ...".

A linguagem SQL possui divisões, a saber:

- DDL - **D**ata **D**efinition **L**anguage - para a criação de componentes de banco dados como tabelas e índices
- DML - **D**ata **M**anipulation **L**anguage - para a manipulação dos dados armazenados no banco de dados
- DQL - **D**ata **Q**uery **L**anguage - para extrair dados do banco de dados
- DCL - **D**ata **C**ontrol **L**anguage - provê a segurança interna do banco de dados

> Exemplos de comandos

| DDL | DML | DQL | DCL |
|:---:|:---:|:---:|:---:|
|CREATE TABEL|INSERT|SELECT|CREATE USER|
|ALTER TABLE|DELETE|---|ALTER USER|
|DROP TABLE|UPDATE|---|GRANT|
|CREATE INDEX|---|---|REVOKE|
|ALTER INDEX |---|---|CREATE SCHEMA|
|DROP INDEX |---|---|---|


Ademais, afim de atender aos objetivos de ensino e aprendizagem apresentados na ementa, aqui serão adotadas as versões SQL-99 e SQL-92. A partir da SQL-99 a linguagem SQL incorpora comandos procedurais[^7] como o *BEGIN*, *IF*, *funções* e *procedimentos* que já existiam como extensões da linguagem. Essas duas revisões, padrão ISO-ANSI, são facilmente encontradas no mercado de desenvolvimento de sistemas sem, portanto, nenhum prejuizo para o aluno no decorrer do curso técnico de informática.

Para falarmos de banco de dados, SQL, SGBDR e sistemas de banco de dados relacionais (*SBDR*) usamos varias fezes a palavra "**dado**", sem, contudo, defini-la neste contexto da Tecnologia da Informação - *TI*[^8]. Agora vejamos o que é o dado o que está em seu entorno.

O dado pode ser abstraido como a unidade básica da informação. Sendo um componente básico de um arquivo em um sistema de arquivos é o *item de dados* a menor unidade carregada de significado no mundo real. Não obstante a isso, pode-se apresentar como exemplo *nome*, *sobrenome*, *telefone*, *número de identificação*, *sigla de partido político* etc.

Mas a informação precisa do dado para ser definida, sendo então, o conjunto de dados relacionados logicamente, tratados como uma unidade isolada por uma aplicação e chamada de **registro**. A informação pode, facilmente ser percebida quando, no mundo real alguém faz um pedido, classifica a profissão de uma pessoa, descreve um produto etc.

Por sua vez, o arquivo é uma coleção de registros de um mesmo tipo. Em uma galeria comercial pode-se dizer que tem lojas de artigos infantis, por exemplo, e que, portanto, o nome do arquivo poderia ser galeria comercia; e o conjunto de itens dado seria o nome, rua, número, especialização, marca, telefone, CNPJ etc.

Dai, o que se tem é um sistema de banco de dados que baseia-se em arquivos e, quando associado aos aspectos relacionais que deve gerenciar, suas definições se expandem:

|item de dados|registro|arquivo|
|----------|:----:|:--|
|coluna ou atributo|linha ou tupla|tabela|

O *banco de dados* é mais complexo. A partir do que já foi visto até aqui pode-se adotar a definição de Toby [et al, 2] para banco de dados: "é uma coleção de dados armazenados e inter-relacionados, [...] de muitos tipos de tabelas."

Para poder manipular esses dados em suas tabelas, utiliza-se uma ferramenta chamada SGBD. Em sintese os SGBDs adimitem uma visão lógica, visão física, linguagem de definição de dados, linguagem de manipulação de dados e utilitário importantes. Aqui useremos um SGBDR por ter maior independência de dados. Essa característica, tão importante, o destacou de seus antecessores, o SGBD hierárquico e o de rede, por trazer a capacidade de mudar a estrutura lógica ou física de um certo banco de dados sem ter que reprogramar os programas de aplicação.

# o Ciclo de vida

O ciclo de vida de um banco de dados incorpora os passos básico envolvidos no projeto de um esquema global do banco de dados lógico, a alocação de dados por uma rede de computadores e a definição de esquemas locais específicos do SGBDR.

1. **Análise de requisitos.** Os requisitos do banco de dados são determidados por meio de entrevistas com os produtores e os usuários dos dados. A ideia e elicitar o fato concreto do mundo real a fim de criar um *mini mundo*, um recorte da realidade que será criado no mundo virtual, nesse contexto é o computador.
2. **Modelo conceitual de dados**. Essa etapa também é conhecida como *projeto lógico* por ter um esquema global com um diagrama de modelo de dados conceitual que mostra todos os dados e seus relacionamentos que ao final será transformado em tabelas. Nesse projeto lógico podemos classificar as fazes em *a*, *b*, *c* e *d* como instrumento didático, a saber.
    a. **modelagem conceitual de dados** é a *analise* dos requisitos por meio de digramas de *ER* ou *UML*.
    b. **integração da visão** quando o projeto é grande e mais de uma pessoa está envolvida na *analise* dos requisitos surgem várias visões dos dados e relacionamentos que devem serracionalisadas e concluidas em uma única visão global.
    c. **tranformação do modelo conceitual em tabelas SQL** é feita por meio de uma categorização das construções de *modelagem de dados* e um conjunto de regras de mapeamento onde cada *relacionamento* e suas *entidades* associadas são transformadas em um conjunto de *tabelas* candidatas específicas do SGBDR.
    d. **normalização de tabelas** é o processo de divisão de uma tabela candidata específica em tabelas menores a fim de eliminar **dependências funcionais** [^9].
3. **Projeto físico**. Aqui o que se quer é uma representação precisa da realidade. o projeto implica em selecionar *índices*, realizar *particionamento*, *clustering* e *desnormalizar*.
4. **Implementação, monitoração e modificação do banco de dados**. Quando o projeto é concluido o banco de dados pode ser criado por meio de uma DDL de um SGBDR. O banco pode ser manipulado por uma DML e consultado com uma DQL. Poderá ainda ser migrado de um SGBDR para outro e realizar DCL.

Trabalhe metodicamente pelas etapas do ciclo de vida e corrija erros de projeto o mais rápido possível, voltamdo a etapa enterior e testando novas alternativas e separe bem o  projeto lógico do projeto físico, pois eles são dicotômicos:

- o projeto lógico visa uma solução viável para satisfazer todas as consultas conhecidas e em potencial.
- o projeto físico é para otimizar o desempenho para consultas e atualizações conhecidas e projetadas.

# Exercícios

1. Pesquise a fim de conhecer e determinar o que é banco de dados *hierárquico*, *rede*, *relacional*, *objeto-relacional* e *objeto*.

2. O que é uma entidade na abordagem relacional?

3. Dê exemplos de entidades.

4. Classifique as entidades.

5. O que é um atributo na abordagem relacional?

6. Exemplifique atributos.

7. O que é uma tupla na abordagem relacional?

9. o que é SGBD?

10. Apresente 3 exemplos de SGBD e suas principais características.

11. Em TI por que é importante o descolamento ou desacoplamento?

12. O que é independência de dados?

13. O que é uma chave?

14. Para que serve a linguagem SQL?

15. O que é GRANT e REVOKE em DCL?  

16. Qual a diferença entre sistema de banco de dados e sistema gerenciados de banco de dados?

17. Faça um diagrama que ilustre a resposta da questão 16.

18. por que a linguagem SQL não é considerada uma linguagem procedural?

19. como instalar um SGBD em um sistema operacional?

20. o que é clustering?

[Voltar ao topo (Conceitos)](#conceitos)

[^1]: [História da IBM](http://www-03.ibm.com/ibm/history/interactive/index.html)
[^2]: [E. F. Codd: A relational model of data for large shared data banks](http://www.seas.upenn.edu/~zives/03f/cis550/codd.pdf?cm_mc_uid=53564730589415039457967&cm_mc_sid_50200000=1503945796)
[^3]: [40 anos SGBDR](https://www.ibm.com/developerworks/community/blogs/ctaurion/entry/40_anos_de_sgbr27?lang=en)
[^4]: [ISO](https://www.iso.org/search/x/query/ISO%252FIEC%25209075)
[^5]: [Celso Henrique Poderoso de Oliveira](https://www.novatec.com.br/autores/celsopoderoso.php)
[^6]: [Projeto e Modelagem de Banco de Dados](https://www.elsevier.com/books/projeto-e-modelagem-de-banco-de-dados/lightstone/978-85-352-6445-6)
[^7]: o paradigma procedural define ***como algo deve ser feito*** em cada linha da sequência de ações.
[^8]: [TI](https://pt.wikipedia.org/wiki/Tecnologia_da_informa%C3%A7%C3%A3o)
[^9]: representa a dependência entre elementos de dados que são identificadores exclusivos (chaves).
