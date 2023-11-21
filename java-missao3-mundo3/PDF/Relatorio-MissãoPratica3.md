<style>
.custom-font {
font-family:  'Arial', sans-serif;
}
</style>

<div  class="custom-font">

<p  align="center">
<img  src="https://i.pinimg.com/originals/1a/21/6f/1a216fb0afdce66e7ffd9c9dbfce393b.jpg"  alt="Descrição da Imagem"  width="200"/></p>
<h2  align="center">Criação de aplicativo Java, com acesso ao banco de dados SQL Server através do middleware JDBC </h2>
<h3  align="center">Missão Prática | Nível 3 | Mundo 3</h3>

* **Aluno:** Matheus Bicalho Costa Lemberg
* **Matrícula:** 202208610773
* **Campus:** Santa inês
* **Curso:** Desenvolvimento Full-Stack
* **Disciplina:** Nível 3: Back-end Sem Banco Não Tem
* **Turma:** 2022.3
* **Semestre Letivo:** 3º Semestre
* **Repositório GitHub:** [Repositório GitHub](https://github.com/MatheusBicalho/estacio-mundo3-missao3)
  

## Objetivo da Prática
Implementar persistência com base no middleware JDBC.
Utilizar o padrão DAO (Data Access Object) no manuseio de dados.
Implementar o mapeamento objeto-relacional em sistemas JAVA.
Server na persistência.
Aplicativo cadastral com uso do SQL.

## Códigos:
    Todos os códigos estão no repositório abaixo:

    https://github.com/MatheusBicalho/estacio-mundo3-missao3
    
```
user=loja
password=loja
dburl=jdbc:sqlserver://localhost:1433;databaseName=loja;encrypt=true;trustServerCertificate=true;

```
## Análise e Conclusão

### Qual a importância dos componentes de middleware, como o JDBC?
Os elementos de middleware, como o JDBC, são fundamentais para simplificar a complexidade associada ao acesso a bancos de dados. Eles oferecem uma interface padronizada, permitindo a interação com distintos tipos de bancos de dados. Essa abordagem simplifica o desenvolvimento de aplicações Java, possibilitando uma comunicação eficaz e segura com o banco de dados, independentemente do sistema específico utilizado..

### Qual a diferença no uso de Statement ou PreparedStatement para a manipulação de dados?
A diferença crucial entre Statement e PreparedStatement está na eficiência e segurança que oferecem. O PreparedStatement é pré-compilado e viabiliza a definição de parâmetros, tornando-o mais veloz e seguro contra ameaças de SQL Injection. Por outro lado, o Statement é mais indicado para consultas SQL estáticas, sem parâmetros definidos, contudo, é menos eficiente e mais suscetível a ataques de injeção de SQL.

### Como o padrão DAO melhora a manutenibilidade do software?
O padrão DAO (Data Access Object) desvincula a lógica de acesso aos dados das demais partes da aplicação, diminuindo a interdependência entre as camadas de negócio e de persistência. Essa abordagem simplifica a manutenção e a escalabilidade do software, uma vez que ajustes na base de dados ou na lógica de acesso aos dados podem ser efetuados com mínimo impacto sobre o restante do código.

### Como a herança é refletida no banco de dados, quando lidamos com um modelo estritamente relacional?
Em um modelo estritamente relacional, a herança pode ser tratada por tabelas separadas para cada classe ou por uma tabela única que inclui colunas para todas as propriedades das classes na hierarquia. Isso requer cuidado na modelagem e no mapeamento objeto-relacional para garantir integridade e bom desempenho do banco de dados.

### Quais as diferenças entre a persistência em arquivo e a persistência em banco de dados?
A persistência em arquivo é geralmente mais simples, embora menos eficiente e segura. É mais adequada para dados menos complexos e que requerem menos operações de busca e atualização. Já a persistência em banco de dados oferece recursos avançados para gerenciamento, segurança e otimização de dados. É mais indicada para dados complexos e para aplicações que demandam transações e consultas sofisticadas.

### Como o uso de operador lambda simplificou a impressão dos valores contidos nas entidades, nas versões mais recentes do Java?
O emprego de operadores lambda nas versões recentes do Java simplificou a impressão dos valores presentes nas entidades, viabilizando a implementação concisa e expressiva de operações em coleções. Com lambdas, torna-se viável realizar iterações e operações sobre os elementos das coleções de maneira mais direta e legível, o que aprimora a clareza do código e reduz a quantidade necessária de linhas de código.

### Por que métodos acionados diretamente pelo método main, sem o uso de um objeto, precisam ser marcados como static?
Métodos chamados diretamente pelo método main precisam ser marcados como static porque o main é um método estático e, por definição, só pode chamar diretamente outros métodos estáticos. Os métodos estáticos pertencem à classe, não às instâncias de objetos, o que possibilita seu acesso sem a necessidade de criar uma instância da classe.