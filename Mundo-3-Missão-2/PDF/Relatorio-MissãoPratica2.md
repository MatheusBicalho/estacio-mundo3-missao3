
<style>
.custom-font {
font-family:  'Arial', sans-serif;
}
</style>
<div  class="custom-font">

<p  align="center">
<img  src="https://i.pinimg.com/originals/1a/21/6f/1a216fb0afdce66e7ffd9c9dbfce393b.jpg"  alt="Descrição da Imagem"  width="210"/></p>
<h2  align="center">Implementação de Banco de Dados para Gerenciamento de Movimentos de Compra e Venda </h2>
<h3  align="center">Missão Prática | Mundo 3 | Nivel 2 </h3>  
 
*   **Aluno:** Matheus Bicalho Costa Lemberg
*   **Matrícula:** 202208610773
*   **Campus:** Santa Inês
*   **Curso:** Desenvolvimento Full-Stack
*   **Disciplina:** Nível 2: Vamos Manter as Informações?
*   **Turma:** 2022.3
*  **Semestre Letivo:** 3º Semestre
*   **Repositório GitHub:** [Link do Repositório GitHub](https://github.com/MatheusBicalho/estacio-mundo3-missao2)
  

## Objetivo da Prática
Esta prática tem como objetivo a criação de um banco de dados relacional para o gerenciamento de movimentos de compra e venda dentro de uma plataforma de negociações, utilizando SQL Server Management Studio e aplicando conceitos de modelagem UML e SQL.

## 👉 1º Procedimento – Criando o Banco de Dados

#### Definição do Modelo de Dados
A estrutura do banco de dados é projetada seguindo o diagrama de classe UML, definindo as entidades `Usuario`, `Pessoa`, `PessoaFisica`, `PessoaJuridica`, `Produto`, `MovimentoCompra`, e `MovimentoVenda`, cada uma com seus atributos e relações, exemplificando a organização e relacionamentos entre as tabelas.

#### Criação da Base de Dados


```sql

CREATE  TABLE  Usuario (
idOperador INT  PRIMARY KEY,
nome VARCHAR(255),
senha VARCHAR(255)
);

CREATE  TABLE  Pessoa (
idPessoa INT  PRIMARY KEY,
nome VARCHAR(255),
logradouro VARCHAR(255),
cidade VARCHAR(255),
estado CHAR(2),
telefone VARCHAR(11),
email VARCHAR(255)
);

CREATE  TABLE  PessoaFisica (
idPessoaFisica INT  PRIMARY KEY,
cpf VARCHAR(11),
FOREIGN KEY (idPessoaFisica) REFERENCES Pessoa(idPessoa)
);

CREATE  TABLE  PessoaJuridica (
idPessoaJuridica INT  PRIMARY KEY,
cnpj VARCHAR(14),
FOREIGN KEY (idPessoaJuridica) REFERENCES Pessoa(idPessoa)
);

CREATE  TABLE  Produto (
idProduto INT  PRIMARY KEY,
nome VARCHAR(255),
quantidade INT,
precoVenda NUMERIC
);

CREATE  TABLE  PessoaFisica (
idPessoaFisica INT  PRIMARY KEY,
cpf VARCHAR(11),
FOREIGN KEY (idPessoaFisica) REFERENCES Pessoa(idPessoa)
);

CREATE  TABLE  MovimentoVenda (
idMovimentoVenda INT  PRIMARY KEY,
quantidade INT,
precoUnitario NUMERIC,
idProduto INT,
idComprador INT,
idOperador INT,
FOREIGN KEY (idProduto) REFERENCES Produto(idProduto),
FOREIGN KEY (idComprador) REFERENCES PessoaFisica(idPessoaFisica),
FOREIGN KEY (idOperador) REFERENCES Usuario(idOperador)
);

CREATE  TABLE  MovimentoCompra (
idMovimentoCompra INT  PRIMARY KEY,
quantidade INT,
precoUnitario NUMERIC,
idProduto INT,
idFornecedor INT,
idOperador INT,
FOREIGN KEY (idProduto) REFERENCES Produto(idProduto),
FOREIGN KEY (idFornecedor) REFERENCES PessoaJuridica(idPessoaJuridica),
FOREIGN KEY (idOperador) REFERENCES Usuario(idOperador)
);

CREATE  SEQUENCE  PessoaIdSequence
START  WITH  1
INCREMENT BY  1;


## Análise e Conclusão

### Como são implementadas as diferentes cardinalidades, basicamente 1X1, 1XN ou NxN, em um banco de dados relacional?

Cardinalidades em bancos de dados relacionais são implementadas da seguinte forma:

- **1X1 (Um para Um):** Quando uma unidade está ligada a, no máximo, outra unidade, é formado esse tipo de vínculo. Normalmente, isso se concretiza utilizando identificadores principais e secundários que se correspondem ou por imposições de singularidade.

- **1XN (Um para Muitos):** Na dinâmica de um para muitos, acontece quando uma instância pode se conectar com múltiplas instâncias de outra categoria. Isso se concretiza mediante o uso de uma referência externa na categoria "muitos", direcionada à referência principal da categoria "um".

- **NxN (Muitos para Muitos):** Uma conexão muitos para muitos é expressa por meio de uma tabela intermediária que inclui referências externas apontando para os identificadores principais das diferentes entidades em questão.

### Que tipo de relacionamento deve ser utilizado para representar o uso de herança em bancos de dados relacionais?

AA representação da herança em bancos de dados relacionais é comumente realizada por meio de uma estrutura tabular que reflete a conexão "é-um" entre diferentes entidades. Esse processo envolve a criação de uma tabela primária que guarda os atributos compartilhados por todas as entidades, e tabelas secundárias correspondentes a cada subcategoria, contendo características específicas e uma referência a essa tabela principal. Assim, as tabelas secundárias "herdam" os dados da tabela primária, emulando o conceito de herança presente na programação orientada a objetos.

### Como o SQL Server Management Studio permite a melhoria da produtividade nas tarefas relacionadas ao gerenciamento do banco de dados?

O SQL Server Management Studio (SSMS) eleva a eficiência ao disponibilizar uma interface gráfica de fácil compreensão que simplifica a gestão do banco de dados. Ele possibilita a execução de scripts SQL, a configuração da segurança, o monitoramento do desempenho e a manutenção dos bancos de dados. Adicionalmente, fornece ferramentas para automatizar tanto tarefas cotidianas quanto as mais complexas, o que contribui para aprimorar a eficácia e reduzir possíveis equívocos.

## 👉 2º Procedimento – Alimentando a Base

### Alimentação Inicial das Tabelas
  
Incluindo dados nas tabelas:

**Inserção de Usuários:**

```sql
INSERT INTO Usuario (nome, senha) VALUES ('op1', 'op1'), ('op2', 'op2');
```

**Inserção de Produtos:**

```sql
INSERT INTO Produto (idProduto, nome, quantidade, precoVenda) VALUES (1, 'Banana', 100, 5.00);
INSERT INTO Produto (idProduto, nome, quantidade, precoVenda) VALUES (2, 'Laranja', 500, 2.00);
INSERT INTO Produto (idProduto, nome, quantidade, precoVenda) VALUES (3, 'Manga', 800, 4.00);
``` 
## Análise e Conclusão


## a. Quais as diferenças no uso de sequence e identity?

As principais diferenças entre `SEQUENCE` e `IDENTITY` são:

**SEQUENCE**: Trata-se de um recurso desenvolvido e controlado pelo sistema de banco de dados, responsável por produzir uma sequência numérica contínua, independente de uma tabela em particular. Sua utilidade abrange diversas tabelas e permanece inalterada mesmo após a remoção de registros.
- **Flexibilidade:** Uma `SEQUENCE` é um elemento independente que produz uma sequência de números em ordem, sem estar vinculado a uma tabela específica.
- **Reutilização:** Pode ser usada por múltiplas tabelas e colunas.
- **Controle:** Oferece um controle avançado no processo de geração de números, permitindo a definição do valor inicial, do incremento, do valor mínimo e máximo, e a opção de reciclar a sequência conforme necessário.
**IDENTITY**: É uma propriedade de coluna específica de uma tabela que gera automaticamente valores numéricos sequenciais. É restrito a uma coluna em uma tabela e é geralmente reiniciado quando os registros são deletados e a tabela é recriada.

- **Simplicidade:** A propriedade `IDENTITY` é usada para gerar automaticamente valores numéricos sequenciais diretamente em uma coluna de uma tabela.
- **Especificidade:** Está diretamente ligada a uma coluna específica em uma tabela.
- **Facilidade de uso:** É mais fácil de configurar, pois requer menos parâmetros.

## b. Qual a importância das chaves estrangerias para a consistência do banco?

Chaves estrangeiras são essenciais para:

- **Integridade Referencial:** A utilização de chaves estrangeiras é fundamental para assegurar a integridade referencial entre tabelas, garantindo a preservação das relações entre elas.
- **Prevenção de Orfãos:** Impedem a existência de registros "órfãos" em tabelas que dependem de outras para manterem sua integridade e significado.
- **Consistência de Dados:** Asseguram que apenas dados válidos sejam inseridos na tabela que possui a chave estrangeira.

## c.   

Na **Álgebra Relacional**, operadores como `SELECT`, `PROJECT`, `JOIN`, `UNION`, `INTERSECT`, e `DIFFERENCE` são usados para manipular e consultar dados em bancos de dados relacionais.
- **Diferença:** Retorna diferenças entre duas consultas.
- **Produto Cartesiano:** Combina todas as linhas de duas tabelas.
- **Seleção:** Filtragem de linhas.
- **Projeção:** Filtragem de colunas.
- **União:** Combina resultados de duas consultas.
- **Junção:** Combina linhas baseadas em condições de junção.

- **Predicados:** Expressões que retornam verdadeiro ou falso.
- **Quantificadores Universais e Existenciais:** Usados para expressar consultas com condições "para todos" ou "existe".
No **Cálculo Relacional**, utiliza-se uma coleção de operadores lógicos como `AND`, `OR`, `NOT`, e `EXISTS`, que permitem a formulação de consultas baseadas em predicados e condições.

## d. Como é feito o agrupamento em consultas, e qual requisito é obrigatório?

A consulta em SQL emprega a funcionalidade GROUP BY para agrupar registros que compartilham os mesmos valores em colunas específicas.
  
- **Requisito Obrigatório**: Quando utilizado, todas as colunas listadas na cláusula `SELECT` que não estão incluídas nas funções agregadas (`COUNT`, `MAX`, `MIN`, `SUM`, `AVG`) devem estar presentes na cláusula `GROUP BY`.