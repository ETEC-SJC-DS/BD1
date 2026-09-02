# BD1

**Plano de curso:** Técnico em Desenvolvimento de Sistemas, BD I
**Nível:** Do zero até o nível de provas e atividades práticas

---

## Sumário

1. Introdução a Banco de Dados
2. SGBD
3. Modelo de Dados
4. MER e DER
5. Entidades e Atributos
6. Relacionamentos
7. Cardinalidade
8. Modelo Relacional
9. Chaves
10. Normalização
11. SQL — Introdução
12. DDL — Criação de Banco e Tabelas
13. Restrições / Constraints
14. DML — INSERT
15. DQL — SELECT
16. Filtros e Operadores
17. ORDER BY
18. LIMIT
19. UPDATE
20. DELETE, DROP e TRUNCATE
21. ALTER TABLE
22. Funções de Agregação
23. GROUP BY
24. HAVING
25. JOIN
26. Subconsultas
27. Relacionamentos em SQL
28. Integridade dos Dados
29. Transações
30. Índices
31. Projeto Completo — Sistema Escolar
32. Exercícios para Praticar
33. Gabarito dos Exercícios
34. Questões Estilo Prova da ETEC
35. Gabarito das Questões
36. Erros Comuns de Iniciantes
37. 🧠 Resumão de BD1
38. ⚡ SQL Essencial
39. Glossário

---

# 1. Introdução a Banco de Dados

## O que é dado

**Dado** é um valor bruto, sem interpretação, sem contexto. Por exemplo: `"Maria"`, `17`, `"3B"`.

Sozinhos, esses valores não dizem muita coisa. Eles só ganham sentido quando são organizados e interpretados.

## O que é informação

**Informação** é o dado interpretado dentro de um contexto, que passa a ter significado.

> Exemplo: o dado `17` sozinho não significa nada. Mas "Maria tem 17 anos e está matriculada na turma 3B" é uma **informação**.

## O que é banco de dados

Um **banco de dados** é um conjunto organizado de dados relacionados entre si, armazenado de forma estruturada, que representa informações sobre um determinado domínio (uma escola, uma loja, uma biblioteca, etc.) e que pode ser consultado e manipulado.

## O que é um SGBD

**SGBD** significa **Sistema Gerenciador de Banco de Dados**. É o software responsável por criar, organizar, manter e controlar o acesso a um banco de dados. Exemplos: MySQL, PostgreSQL, Oracle.

## Diferença entre banco de dados e SGBD

Muita gente confunde os dois conceitos. É importante fixar essa diferença desde o começo:

| Conceito | O que é | Exemplo |
|---|---|---|
| Banco de dados | O conjunto de dados em si, organizado em tabelas | As tabelas `alunos`, `cursos`, `matriculas` de uma escola |
| SGBD | O programa que gerencia esse banco de dados | MySQL, PostgreSQL, SQL Server |

**O banco de dados é o "conteúdo"; o SGBD é o "programa" que cuida desse conteúdo.**

## Para que servem bancos de dados

Bancos de dados servem para armazenar, organizar, proteger e permitir a consulta rápida e confiável de grandes quantidades de informação, evitando perda de dados, duplicidade e inconsistência.

## Exemplos de sistemas que utilizam bancos de dados

* Sistemas escolares (matrícula, notas, frequência)
* Sistemas bancários
* E-commerces (produtos, clientes, pedidos)
* Redes sociais
* Sistemas hospitalares
* Aplicativos de transporte

## Vantagens de utilizar bancos de dados

* Redução de redundância (dados repetidos)
* Maior integridade e consistência dos dados
* Controle de acesso e segurança
* Consultas rápidas e complexas
* Possibilidade de múltiplos usuários acessando ao mesmo tempo
* Backup e recuperação facilitados

## Problemas de armazenar informações sem um banco de dados

Muitos sistemas antigos (ou mal planejados) guardam dados em arquivos soltos (planilhas, arquivos texto). Isso costuma gerar:

* **Redundância**: o mesmo dado repetido em vários lugares.
* **Inconsistência**: um mesmo dado com valores diferentes em locais diferentes.
* **Dificuldade de busca**: encontrar uma informação específica é lento.
* **Falta de segurança**: qualquer pessoa pode alterar os arquivos.
* **Falta de controle de acesso simultâneo**: dois usuários editando o mesmo arquivo ao mesmo tempo podem causar perda de dados.

## Banco de dados relacional

Um **banco de dados relacional** organiza os dados em **tabelas** (linhas e colunas), onde cada tabela representa uma entidade do mundo real (por exemplo, `alunos`), e essas tabelas podem se relacionar entre si por meio de chaves. É o modelo mais usado no mercado e é o foco desta apostila.

## Banco de dados não relacional (introdução)

Bancos **não relacionais** (também chamados de **NoSQL**) armazenam dados de outras formas, como documentos (JSON), pares chave-valor, grafos ou colunas, sem a estrutura rígida de tabelas. Exemplos: MongoDB, Redis, Cassandra. Esse tema não é o foco de BD1, mas é importante saber que ele existe.

## Comparação simples

| Conceito | Explicação | Exemplo |
|---|---|---|
| Dado | Valor bruto sem contexto | `17` |
| Informação | Dado interpretado com significado | "Aluno tem 17 anos" |
| Banco de dados | Conjunto organizado de dados | Tabelas de uma escola |
| SGBD | Software que gerencia o banco | MySQL |
| Banco relacional | Organizado em tabelas | MySQL, PostgreSQL |
| Banco não relacional | Organizado de outras formas | MongoDB |

---

# 2. SGBD

## O que é

Como já vimos, o **SGBD (Sistema Gerenciador de Banco de Dados)** é o software que faz a ponte entre o usuário/aplicação e o banco de dados propriamente dito.

## Para que serve

O SGBD é responsável por:

* Criar e organizar tabelas;
* Garantir a integridade dos dados (regras, chaves, restrições);
* Controlar o acesso de múltiplos usuários ao mesmo tempo;
* Executar comandos SQL (inserir, consultar, alterar, excluir dados);
* Fazer backup e recuperação de dados;
* Otimizar o desempenho das consultas.

## Como funciona

O usuário (ou uma aplicação) envia comandos em **SQL** para o SGBD. O SGBD interpreta o comando, executa a operação no banco de dados e devolve um resultado (por exemplo, uma lista de registros).

```
Aplicação → comando SQL → SGBD → Banco de Dados
```

## Principais SGBDs do mercado

| SGBD | Características principais |
|---|---|
| **MySQL** | Gratuito, muito usado em sistemas web, ótimo para aprender |
| **MariaDB** | "Fork" (versão derivada) do MySQL, muito compatível com ele |
| **PostgreSQL** | Gratuito, robusto, com muitos recursos avançados |
| **SQL Server** | Da Microsoft, muito usado em empresas que já usam tecnologias Microsoft |
| **Oracle Database** | Pago, usado em grandes empresas e sistemas corporativos críticos |
| **SQLite** | Muito leve, não precisa de servidor, usado em apps mobile e projetos pequenos |

## Diferenças principais (visão simples)

* **MySQL/MariaDB**: focados em simplicidade e desempenho para aplicações web. É o padrão adotado nesta apostila.
* **PostgreSQL**: mais rigoroso com tipos de dados e com recursos avançados (ótimo para sistemas mais complexos).
* **SQL Server** e **Oracle**: usados principalmente em ambientes corporativos, geralmente pagos.
* **SQLite**: não precisa de um servidor rodando; o banco é um único arquivo. Ótimo para testes e apps pequenos.

## Erros comuns

* Achar que "SQL" e "SGBD" são a mesma coisa (SQL é a **linguagem**; SGBD é o **programa** que interpreta essa linguagem).
* Achar que existe apenas um SGBD "certo" — na prática, a escolha depende do projeto.

## Resumo

O SGBD é o programa que gerencia o banco de dados, executando os comandos SQL e garantindo organização, integridade e segurança dos dados. Existem vários SGBDs no mercado; esta apostila usa como referência o **MySQL/MariaDB**.

---

# 3. Modelo de Dados

## O que é

Um **modelo de dados** é uma forma de representar, organizar e planejar como os dados de um sistema serão estruturados, **antes** de criar o banco de dados de verdade. É como uma planta de uma casa antes de construí-la.

## Para que serve

Serve para planejar o banco de dados de forma organizada, evitando erros de estrutura, redundância e retrabalho.

## Os três níveis de modelagem

### Modelo Conceitual

* É o nível mais **abstrato**, mais próximo da linguagem humana.
* Representa **o quê** existe no sistema (entidades, atributos, relacionamentos), sem se preocupar com tecnologia.
* Normalmente representado pelo **MER/DER**.
* Exemplo: "Existe um Aluno que se matricula em um Curso."

### Modelo Lógico

* É o nível intermediário.
* Já mostra **como** os dados serão organizados em tabelas, colunas, chaves primárias e estrangeiras — mas ainda sem se prender à sintaxe exata de um SGBD específico.
* Exemplo: tabela `aluno(id_aluno, nome, data_nascimento)`.

### Modelo Físico

* É o nível mais **concreto**.
* Representa como o banco será implementado de fato em um SGBD específico, com tipos de dados exatos, constraints, índices etc.
* Exemplo: o comando `CREATE TABLE` já pronto em SQL para o MySQL.

## Comparação

| Modelo | Nível | Preocupação | Exemplo |
|---|---|---|---|
| Conceitual | Abstrato | O quê existe | Entidade Aluno, Entidade Curso |
| Lógico | Intermediário | Como se relacionam | Tabela aluno com FK para curso |
| Físico | Concreto | Como implementar | `CREATE TABLE aluno (...)` no MySQL |

## Exemplo — transformando um problema real em banco de dados

**Problema:** "Preciso guardar os alunos de uma escola, os cursos que eles fazem e as notas que tiram."

1. **Conceitual**: identifico as entidades `Aluno`, `Curso`, `Nota` e como elas se relacionam.
2. **Lógico**: desenho as tabelas `aluno`, `curso`, `matricula` (com `id_aluno` e `id_curso` como chaves estrangeiras).
3. **Físico**: escrevo o `CREATE TABLE` para o MySQL, com os tipos de dados definidos (`INT`, `VARCHAR`, `DECIMAL` etc.).

## Erros comuns

* Pular direto para o SQL sem planejar o modelo conceitual e lógico.
* Confundir o modelo conceitual (que não tem tipos de dados) com o modelo físico.

## Resumo

A modelagem de dados acontece em três etapas: **conceitual** (o quê existe), **lógico** (como se relaciona) e **físico** (como implementar no SGBD). Pular etapas costuma gerar bancos de dados mal planejados.

---

# 4. MER e DER

## O que é o MER

**MER (Modelo Entidade-Relacionamento)** é a técnica usada para representar, no nível conceitual, as **entidades**, seus **atributos** e os **relacionamentos** entre elas.

## O que é o DER

**DER (Diagrama Entidade-Relacionamento)** é a **representação gráfica** do MER. Ou seja: o MER é o *conceito/modelo*, e o DER é o *desenho* desse modelo.

> Resumindo: **MER é a ideia, DER é o desenho da ideia.**

## Para que serve

O DER serve para visualizar, de forma clara, quais entidades existem no sistema, quais atributos elas possuem e como elas se relacionam — antes de qualquer linha de SQL ser escrita.

## Elementos de um DER

| Elemento | Representação tradicional | Significado |
|---|---|---|
| Entidade | Retângulo | Um "objeto" do mundo real (Aluno, Curso) |
| Atributo | Elipse (ou lista dentro do retângulo, na notação simplificada) | Uma característica da entidade (nome, idade) |
| Relacionamento | Losango (ou linha nomeada, na notação simplificada) | Uma associação entre entidades (Aluno **cursa** Curso) |
| Cardinalidade | Números/símbolos na linha do relacionamento | Quantas vezes uma entidade se relaciona com a outra |
| Identificador (chave) | Atributo sublinhado | O atributo que identifica unicamente cada registro |

## Como interpretar um DER

1. Identifique as entidades (os retângulos).
2. Veja os atributos de cada entidade.
3. Observe os relacionamentos (o verbo que liga as entidades, como "cursa", "leciona", "pertence").
4. Leia a cardinalidade nas duas pontas do relacionamento.

## Exemplo de DER — Sistema Escolar (representação textual)

Como este material é em Markdown, representamos o DER de forma textual, indicando como ele seria desenhado graficamente:

```
[ALUNO] ---- (matricula-se) ---- [CURSO]
  |                                  |
  atributos:                    atributos:
  - id_aluno (PK)                - id_curso (PK)
  - nome                         - nome_curso
  - data_nascimento              - carga_horaria

[PROFESSOR] ---- (leciona) ---- [DISCIPLINA]
  |                                  |
  atributos:                    atributos:
  - id_professor (PK)            - id_disciplina (PK)
  - nome                         - nome_disciplina
```

Graficamente, cada entidade (`ALUNO`, `CURSO`, `PROFESSOR`, `DISCIPLINA`) seria um **retângulo**; cada relacionamento (`matricula-se`, `leciona`) seria um **losango** ligando os retângulos; e cada atributo seria uma **elipse** conectada à sua entidade, com a chave primária **sublinhada**.

## Resumo

O DER é a representação gráfica do MER. Ele mostra entidades (retângulos), atributos (elipses) e relacionamentos (losangos), sendo a principal ferramenta para planejar um banco de dados no nível conceitual.

---

# 5. Entidades e Atributos

## O que é uma entidade

Uma **entidade** é qualquer "coisa" do mundo real sobre a qual queremos guardar informações: uma pessoa, um objeto, um evento ou um conceito. No banco de dados, cada entidade normalmente vira uma **tabela**.

> Exemplos: `Aluno`, `Professor`, `Curso`, `Produto`, `Cliente`, `Pedido`.

## O que é um atributo

Um **atributo** é uma característica/propriedade de uma entidade. No banco de dados, cada atributo normalmente vira uma **coluna** da tabela.

> Exemplo: a entidade `Aluno` pode ter os atributos `nome`, `data_nascimento`, `email`.

## Tipos de atributo

### Atributo simples

Não pode ser dividido em partes menores.

> Exemplo: `idade`.

### Atributo composto

Pode ser dividido em partes menores, que também têm significado próprio.

> Exemplo: `endereço` pode ser dividido em `rua`, `número`, `bairro`, `cidade`.

### Atributo multivalorado

Pode ter mais de um valor para a mesma entidade.

> Exemplo: um `Aluno` pode ter mais de um `telefone`. Na prática, isso normalmente vira uma **tabela separada** no modelo relacional (veremos isso na normalização).

### Atributo derivado

É calculado a partir de outro atributo, não precisando ser armazenado diretamente.

> Exemplo: a `idade` pode ser derivada da `data_nascimento`. Em vez de guardar a idade (que muda todo ano), guarda-se a data de nascimento e calcula-se a idade quando necessário.

## Exemplo aplicado

Entidade `Aluno`:

| Atributo | Tipo |
|---|---|
| id_aluno | Simples (chave) |
| nome | Simples |
| endereço | Composto (rua, número, bairro) |
| telefone | Multivalorado |
| idade | Derivado (a partir da data de nascimento) |

## Erros comuns

* Confundir entidade com atributo (ex.: tratar "Curso" como um atributo de Aluno, quando na verdade é uma entidade própria).
* Tentar guardar um atributo multivalorado em uma única coluna separada por vírgulas (isso fere a normalização, como veremos mais à frente).

## Resumo

Entidades são "coisas" do mundo real que viram tabelas; atributos são características dessas entidades que viram colunas. Atributos podem ser simples, compostos, multivalorados ou derivados.

---

# 6. Relacionamentos

## O que é

Um **relacionamento** é uma associação entre duas (ou mais) entidades. Ele representa como as entidades se conectam no mundo real.

> Exemplo: `Aluno` **matricula-se em** `Curso`.

## Tipos de relacionamento

### 1:1 (um para um)

Cada registro de uma entidade se relaciona com **no máximo um** registro da outra entidade, e vice-versa.

> Exemplo: um `Professor` possui uma `Sala` exclusiva, e cada sala pertence a um único professor.

**Como representar em tabelas:** a chave estrangeira (FK) pode ficar em qualquer uma das duas tabelas (geralmente na que "depende" mais da outra), com uma constraint `UNIQUE` para garantir que a relação seja de fato 1:1.

```sql
CREATE TABLE professor (
    id_professor INT PRIMARY KEY,
    nome VARCHAR(100)
);

CREATE TABLE sala (
    id_sala INT PRIMARY KEY,
    numero VARCHAR(10),
    id_professor INT UNIQUE,
    FOREIGN KEY (id_professor) REFERENCES professor(id_professor)
);
```

### 1:N (um para muitos)

Um registro de uma entidade pode se relacionar com **vários** registros da outra, mas cada registro da segunda entidade se relaciona com **apenas um** registro da primeira.

> Exemplo: um `Curso` tem vários `Alunos`, mas cada `Aluno` (nesse exemplo simplificado) pertence a apenas um `Curso`.

**Como representar em tabelas:** a chave estrangeira fica sempre do **lado "muitos"** (no exemplo, na tabela `aluno`).

```sql
CREATE TABLE curso (
    id_curso INT PRIMARY KEY,
    nome_curso VARCHAR(100)
);

CREATE TABLE aluno (
    id_aluno INT PRIMARY KEY,
    nome VARCHAR(100),
    id_curso INT,
    FOREIGN KEY (id_curso) REFERENCES curso(id_curso)
);
```

### N:N (muitos para muitos)

Vários registros de uma entidade podem se relacionar com vários registros da outra entidade.

> Exemplo: um `Aluno` pode se matricular em vários `Cursos`, e um `Curso` pode ter vários `Alunos` matriculados.

**Por que é necessária uma tabela intermediária?**

Em um banco relacional, **não é possível** representar diretamente um relacionamento N:N apenas com uma FK em uma das tabelas, porque uma coluna não pode guardar "vários valores" ao mesmo tempo sem ferir a normalização. A solução é criar uma **tabela associativa** (também chamada de tabela intermediária ou tabela de junção), que guarda os pares de IDs relacionados.

```sql
CREATE TABLE aluno (
    id_aluno INT PRIMARY KEY,
    nome VARCHAR(100)
);

CREATE TABLE curso (
    id_curso INT PRIMARY KEY,
    nome_curso VARCHAR(100)
);

CREATE TABLE matricula (
    id_aluno INT,
    id_curso INT,
    data_matricula DATE,
    PRIMARY KEY (id_aluno, id_curso),
    FOREIGN KEY (id_aluno) REFERENCES aluno(id_aluno),
    FOREIGN KEY (id_curso) REFERENCES curso(id_curso)
);
```

Aqui, a tabela `matricula` guarda cada combinação de aluno + curso, permitindo que um aluno tenha várias linhas (uma para cada curso) e um curso tenha várias linhas (uma para cada aluno).

## Resumo comparativo

| Tipo | Exemplo | Onde fica a FK |
|---|---|---|
| 1:1 | Professor ↔ Sala | Em uma das tabelas, com UNIQUE |
| 1:N | Curso ↔ Alunos | No lado "N" (muitos) |
| N:N | Aluno ↔ Cursos | Em uma tabela intermediária |

## Erros comuns

* Tentar representar um relacionamento N:N com uma FK direta, o que é impossível sem duplicar dados.
* Colocar a FK do lado errado em um relacionamento 1:N (a FK sempre fica do lado "muitos").
* Esquecer de colocar `UNIQUE` na FK de um relacionamento 1:1, o que faria o banco aceitar, sem querer, um relacionamento 1:N.

## Resumo

Relacionamentos conectam entidades e podem ser 1:1, 1:N ou N:N. O relacionamento N:N sempre exige uma tabela intermediária (associativa) para ser implementado corretamente em um banco relacional.

---

# 7. Cardinalidade

## O que é

**Cardinalidade** indica **quantas vezes** um registro de uma entidade pode se relacionar com registros da outra entidade. Ela é representada por um par de números: **mínimo** e **máximo**.

## Cardinalidade mínima

Indica se a participação no relacionamento é **obrigatória** ou **opcional**:

* **0** → participação opcional (pode ou não existir relação);
* **1** → participação obrigatória (deve existir pelo menos uma relação).

## Cardinalidade máxima

Indica o **limite superior** de relações:

* **1** → no máximo uma relação;
* **N** → pode haver várias relações.

## Combinações mais comuns

| Notação | Significado | Exemplo |
|---|---|---|
| 0..1 | Opcional, no máximo um | Um aluno **pode ou não** ter um responsável cadastrado; se tiver, é só um |
| 1..1 | Obrigatório, exatamente um | Todo aluno **deve ter** exatamente uma matrícula ativa |
| 0..N | Opcional, pode ter vários | Um professor **pode não lecionar** nenhuma disciplina, ou pode lecionar várias |
| 1..N | Obrigatório, pode ter vários | Um curso **deve ter** pelo menos um aluno matriculado (ou mais) |

## Como descobrir a cardinalidade fazendo perguntas

Uma boa técnica é fazer perguntas nos dois sentidos do relacionamento:

> Relacionamento: `Aluno` — matricula-se — `Curso`

1. "Um aluno pode se matricular em quantos cursos, no mínimo e no máximo?" → resposta define a cardinalidade do lado **Curso**.
2. "Um curso pode ter quantos alunos matriculados, no mínimo e no máximo?" → resposta define a cardinalidade do lado **Aluno**.

Se a resposta for "de zero a vários", a cardinalidade é **0..N**. Se for "obrigatoriamente um e só um", é **1..1**. E assim por diante.

## Exemplo completo

```
[ALUNO] (0,N) ---- matricula-se ---- (1,N) [CURSO]
```

Interpretação:

* Um `Aluno` pode estar matriculado em **zero a vários** cursos (0,N).
* Um `Curso` deve ter **pelo menos um** aluno matriculado, podendo ter vários (1,N).

## Exercícios de interpretação

1. `[PROFESSOR] (0,N) ---- leciona ---- (1,1) [DISCIPLINA]` — o que isso significa sobre quantas disciplinas um professor pode lecionar, e quantos professores uma disciplina pode ter?
2. `[CLIENTE] (1,1) ---- realiza ---- (0,N) [PEDIDO]` — um pedido pode existir sem cliente? Um cliente é obrigado a fazer pedidos?
3. `[LIVRO] (0,1) ---- emprestado_para ---- (0,N) [ALUNO]` — um livro pode estar emprestado para mais de um aluno ao mesmo tempo?

*(As respostas comentadas estão na seção de Gabarito, junto com os demais exercícios.)*

## Erros comuns

* Trocar a ordem da leitura (ler a cardinalidade do lado errado do relacionamento).
* Confundir cardinalidade **mínima** (obrigatoriedade) com cardinalidade **máxima** (quantidade).

## Resumo

A cardinalidade define quantas vezes uma entidade se relaciona com a outra, sempre com um valor mínimo (obrigatoriedade: 0 ou 1) e um valor máximo (limite: 1 ou N).

---

# 8. Modelo Relacional

## O que é

O **modelo relacional** organiza os dados em **tabelas** (também chamadas de **relações**), compostas por **linhas** e **colunas**. É o modelo mais usado nos SGBDs tradicionais (MySQL, PostgreSQL, SQL Server, Oracle).

## Conceitos e seus "apelidos"

Um mesmo conceito pode ter nomes diferentes dependendo do contexto (mais formal/acadêmico ou mais prático):

| Termo formal | Termo prático | Significado |
|---|---|---|
| Relação | Tabela | Conjunto de dados organizados em linhas e colunas |
| Tupla | Registro / Linha | Um conjunto de valores relacionados (um "item" da tabela) |
| Atributo | Campo / Coluna | Uma característica armazenada (nome, idade etc.) |
| Domínio | — | O conjunto de valores válidos que um atributo pode assumir |

## Exemplo de tabela

Tabela `aluno`:

| id_aluno | nome | idade |
|---|---|---|
| 1 | Maria Silva | 17 |
| 2 | João Souza | 18 |
| 3 | Ana Costa | 16 |

* Cada **linha** (1, 2, 3) é uma **tupla/registro**.
* Cada **coluna** (`id_aluno`, `nome`, `idade`) é um **atributo/campo**.
* O **domínio** do atributo `idade`, por exemplo, poderia ser definido como "números inteiros entre 14 e 25".

## Chave primária (Primary Key — PK)

É o atributo (ou conjunto de atributos) que identifica **de forma única** cada registro de uma tabela. Não pode se repetir e não pode ser nulo.

> No exemplo acima, `id_aluno` é a chave primária.

## Chave estrangeira (Foreign Key — FK)

É um atributo que faz referência à chave primária de **outra** tabela, criando um relacionamento entre elas.

> Exemplo: na tabela `matricula`, o campo `id_aluno` é uma FK que aponta para `aluno.id_aluno`.

## Chaves candidatas

São todos os atributos (ou conjuntos de atributos) que **poderiam** ser escolhidos como chave primária, por também identificarem unicamente cada registro. Apenas uma delas é escolhida como PK; as demais continuam sendo chaves candidatas.

> Exemplo: em uma tabela `aluno`, tanto `id_aluno` quanto `cpf` poderiam ser chave primária (ambos são únicos). Se escolhermos `id_aluno` como PK, o `cpf` continua sendo uma chave candidata.

## Chave composta

É uma chave primária formada por **mais de um atributo**, usada quando nenhum atributo isolado identifica o registro de forma única.

> Exemplo: na tabela `matricula`, a combinação de `id_aluno` + `id_curso` forma a chave composta, pois cada aluno pode estar em vários cursos e vice-versa, mas a combinação dos dois é única.

## Integridade referencial

É a regra que garante que uma **chave estrangeira** sempre aponte para um valor **existente** na tabela referenciada (ou seja, nulo, se permitido). Ela impede, por exemplo, que exista uma matrícula referenciando um `id_aluno` que não existe na tabela `aluno`.

## Erros comuns

* Confundir chave primária com chave estrangeira (a PK identifica o próprio registro; a FK aponta para o registro de outra tabela).
* Esquecer de declarar `PRIMARY KEY`, permitindo registros duplicados.
* Não respeitar a integridade referencial, criando "FKs órfãs" (que apontam para registros inexistentes).

## Resumo

O modelo relacional organiza dados em tabelas (relações), formadas por linhas (tuplas) e colunas (atributos). As chaves primária e estrangeira são fundamentais para identificar registros e conectar tabelas, respeitando a integridade referencial.

---

# 9. Normalização

## O motivo da normalização

**Normalização** é o processo de organizar as tabelas de um banco de dados para reduzir **redundância** (dados repetidos) e evitar **anomalias** (problemas ao inserir, atualizar ou excluir dados).

## Problemas que a normalização resolve

* **Redundância**: o mesmo dado aparece repetido em várias linhas.
* **Inconsistência**: por causa da redundância, o mesmo dado pode ficar com valores diferentes em lugares diferentes (ex.: o nome de um curso escrito de duas formas diferentes).
* **Anomalia de inserção**: dificuldade ou impossibilidade de inserir um dado sem precisar inserir outro junto (ex.: não conseguir cadastrar um curso novo porque a tabela exige um aluno matriculado).
* **Anomalia de atualização**: necessidade de atualizar o mesmo dado em várias linhas (ex.: mudar o nome de um curso em 50 linhas diferentes).
* **Anomalia de exclusão**: perder informações importantes ao excluir um registro (ex.: excluir o único aluno de um curso e, sem querer, perder também os dados do curso).

## Primeira Forma Normal (1FN)

**Regra:** cada coluna deve conter apenas **valores atômicos** (indivisíveis), e não deve haver **grupos repetidos** (várias colunas do mesmo tipo, como `telefone1`, `telefone2`).

### Tabela errada (fere a 1FN)

| id_aluno | nome | telefones |
|---|---|---|
| 1 | Maria Silva | 11999990000, 11988880000 |

**Problema:** a coluna `telefones` guarda mais de um valor na mesma célula, o que dificulta buscas e atualizações.

### Correção

Criar uma tabela separada para os telefones:

**aluno**

| id_aluno | nome |
|---|---|
| 1 | Maria Silva |

**telefone_aluno**

| id_telefone | id_aluno | numero |
|---|---|---|
| 1 | 1 | 11999990000 |
| 2 | 1 | 11988880000 |

## Segunda Forma Normal (2FN)

**Regra:** a tabela já deve estar na 1FN, e **todos os atributos não-chave devem depender da chave primária completa** (isso só é relevante quando a chave primária é **composta**).

### Tabela errada (fere a 2FN)

Tabela `matricula` com chave composta (`id_aluno`, `id_curso`):

| id_aluno | id_curso | nome_aluno | nome_curso | data_matricula |
|---|---|---|---|---|

**Problema:** `nome_aluno` depende apenas de `id_aluno` (não da chave composta inteira), e `nome_curso` depende apenas de `id_curso`. Isso gera redundância (o nome do aluno se repete em cada matrícula).

### Correção

Separar em três tabelas:

**aluno**(id_aluno, nome_aluno)
**curso**(id_curso, nome_curso)
**matricula**(id_aluno, id_curso, data_matricula)

Agora, `nome_aluno` e `nome_curso` ficam apenas em suas tabelas de origem, e `matricula` guarda somente os dados que realmente dependem da combinação aluno+curso.

## Terceira Forma Normal (3FN)

**Regra:** a tabela já deve estar na 2FN, e **não pode haver dependência transitiva** — ou seja, um atributo não-chave não pode depender de outro atributo não-chave (só pode depender da chave primária).

### Tabela errada (fere a 3FN)

| id_aluno | nome | id_curso | nome_curso |
|---|---|---|---|
| 1 | Maria | 10 | Desenvolvimento de Sistemas |
| 2 | João | 10 | Desenvolvimento de Sistemas |

**Problema:** `nome_curso` depende de `id_curso`, que **não é a chave primária** da tabela `aluno` — é um atributo não-chave. Isso é uma dependência transitiva: `nome_curso` depende de `id_curso`, que depende de `id_aluno`.

### Correção

Separar em duas tabelas:

**aluno**(id_aluno, nome, id_curso)
**curso**(id_curso, nome_curso)

Agora `nome_curso` só existe na tabela `curso`, eliminando a dependência transitiva.

## Resultado final normalizado (exemplo completo)

```sql
CREATE TABLE curso (
    id_curso INT PRIMARY KEY,
    nome_curso VARCHAR(100)
);

CREATE TABLE aluno (
    id_aluno INT PRIMARY KEY,
    nome VARCHAR(100),
    id_curso INT,
    FOREIGN KEY (id_curso) REFERENCES curso(id_curso)
);

CREATE TABLE telefone_aluno (
    id_telefone INT PRIMARY KEY,
    id_aluno INT,
    numero VARCHAR(20),
    FOREIGN KEY (id_aluno) REFERENCES aluno(id_aluno)
);
```

> **Observação:** para BD1, normalmente é suficiente entender bem até a **3FN**. Formas normais mais avançadas (BCNF, 4FN, 5FN) não costumam ser cobradas neste módulo.

## Erros comuns

* Achar que normalizar significa "criar o máximo de tabelas possível" sem entender o motivo.
* Confundir 2FN com 3FN (a 2FN trata de dependência da chave composta; a 3FN trata de dependência entre atributos não-chave).
* Deixar dados repetidos "para facilitar" — isso quase sempre gera inconsistência no futuro.

## Resumo

A normalização organiza as tabelas para eliminar redundância e anomalias. A 1FN exige valores atômicos; a 2FN exige que atributos dependam da chave composta inteira; a 3FN exige que não haja dependência entre atributos não-chave.

---

# 10. SQL — Introdução

## O que é SQL

**SQL (Structured Query Language)** é a linguagem padrão usada para criar, consultar, alterar e gerenciar dados em bancos de dados relacionais.

## Para que serve

Serve para o usuário (ou aplicação) se comunicar com o SGBD: criar tabelas, inserir dados, buscar informações, atualizar registros e excluir dados.

## Categorias da linguagem SQL

| Categoria | Sigla | Função | Comandos principais |
|---|---|---|---|
| Linguagem de Definição de Dados | **DDL** | Define a estrutura do banco | `CREATE`, `ALTER`, `DROP` |
| Linguagem de Manipulação de Dados | **DML** | Manipula os dados dentro das tabelas | `INSERT`, `UPDATE`, `DELETE` |
| Linguagem de Consulta de Dados | **DQL** | Consulta os dados | `SELECT` |
| Linguagem de Controle de Dados | **DCL** | Controla permissões de acesso | `GRANT`, `REVOKE` |
| Linguagem de Controle de Transações | **TCL** | Controla transações | `COMMIT`, `ROLLBACK` |

> **Atenção:** algumas bibliografias colocam o `SELECT` dentro do próprio DML, sem separar o DQL como categoria isolada. Essa classificação pode variar conforme o autor ou o SGBD, mas o **conteúdo prático dos comandos é o mesmo**.

## Resumo

SQL é a linguagem usada para interagir com bancos relacionais, dividida (na visão mais comum) em DDL (estrutura), DML (manipulação), DQL (consulta), DCL (permissões) e TCL (transações).

---

# 11. Criação de Banco e Tabelas (DDL)

## CREATE DATABASE

Cria um novo banco de dados.

```sql
CREATE DATABASE escola;
```

Para começar a usar esse banco:

```sql
USE escola;
```

## CREATE TABLE

Cria uma nova tabela dentro do banco de dados atual.

```sql
CREATE TABLE aluno (
    id_aluno INT PRIMARY KEY AUTO_INCREMENT,
    nome VARCHAR(100) NOT NULL,
    data_nascimento DATE,
    email VARCHAR(100) UNIQUE
);
```

## Tipos de dados comuns

| Tipo | Uso | Exemplo |
|---|---|---|
| `INT` | Números inteiros | idade, quantidade |
| `VARCHAR(n)` | Texto de tamanho variável (até n caracteres) | nome, email |
| `CHAR(n)` | Texto de tamanho **fixo** | sigla de estado (`CHAR(2)`) |
| `TEXT` | Texto longo, sem limite prático de tamanho | descrição, observações |
| `DATE` | Datas (ano-mês-dia) | data de nascimento |
| `DATETIME` | Data e hora | data e hora de um pedido |
| `DECIMAL(p,s)` | Números decimais exatos (p = total de dígitos, s = casas decimais) | preço, nota |
| `BOOLEAN` | Verdadeiro/Falso (no MySQL é tratado como `TINYINT(1)`) | ativo, aprovado |

## Quando usar cada tipo

* Use `VARCHAR` para textos curtos e de tamanho variável (nomes, e-mails).
* Use `CHAR` apenas quando o tamanho é sempre o mesmo (siglas, códigos fixos).
* Use `TEXT` para textos longos (parágrafos, descrições).
* Use `DECIMAL` para valores monetários e notas — **nunca** use `FLOAT`/`DOUBLE` para dinheiro, pois eles têm imprecisão.
* Use `DATE` quando só a data importa; use `DATETIME` quando o horário também é relevante.

## Exemplo — tabela curso

```sql
CREATE TABLE curso (
    id_curso INT PRIMARY KEY AUTO_INCREMENT,
    nome_curso VARCHAR(100) NOT NULL,
    carga_horaria INT
);
```

## Erros comuns

* Usar `VARCHAR` sem definir o tamanho (`VARCHAR` sozinho, sem `(n)`, gera erro em vários SGBDs).
* Usar `FLOAT` para valores monetários (gera erros de arredondamento).
* Esquecer de definir a chave primária.

## Resumo

`CREATE DATABASE` cria o banco; `CREATE TABLE` cria as tabelas, definindo colunas e seus tipos de dados. A escolha correta do tipo de dado evita erros e desperdício de espaço.

---

# 12. Restrições / Constraints

## O que são

**Constraints** são regras aplicadas às colunas de uma tabela para garantir a integridade e a consistência dos dados.

## PRIMARY KEY

Define a chave primária da tabela — identifica cada linha de forma única e não permite valores nulos nem duplicados.

```sql
CREATE TABLE curso (
    id_curso INT PRIMARY KEY,
    nome_curso VARCHAR(100)
);
```

## FOREIGN KEY

Cria uma relação entre a coluna de uma tabela e a chave primária de outra tabela, garantindo a integridade referencial.

```sql
CREATE TABLE aluno (
    id_aluno INT PRIMARY KEY,
    nome VARCHAR(100),
    id_curso INT,
    FOREIGN KEY (id_curso) REFERENCES curso(id_curso)
);
```

## NOT NULL

Impede que a coluna fique sem valor (vazia/nula).

```sql
nome VARCHAR(100) NOT NULL
```

## UNIQUE

Garante que todos os valores daquela coluna sejam diferentes entre si (mas, diferente da PK, permite um valor nulo, dependendo do SGBD).

```sql
email VARCHAR(100) UNIQUE
```

## DEFAULT

Define um valor padrão, usado quando nenhum valor é informado na inserção.

```sql
ativo BOOLEAN DEFAULT TRUE
```

## CHECK

Define uma condição que os valores da coluna devem sempre respeitar.

```sql
nota DECIMAL(4,2) CHECK (nota >= 0 AND nota <= 10)
```

> **Atenção:** versões mais antigas do MySQL aceitavam a sintaxe do `CHECK` mas não a validavam de fato. Isso foi corrigido a partir do MySQL 8.0.16.

## Exemplo completo com várias constraints

```sql
CREATE TABLE matricula (
    id_aluno INT,
    id_curso INT,
    data_matricula DATE NOT NULL,
    status VARCHAR(20) DEFAULT 'ativa',
    PRIMARY KEY (id_aluno, id_curso),
    FOREIGN KEY (id_aluno) REFERENCES aluno(id_aluno),
    FOREIGN KEY (id_curso) REFERENCES curso(id_curso)
);
```

## Por que constraints são importantes

Elas evitam que dados inválidos ou inconsistentes entrem no banco, transferindo parte da responsabilidade de "validar os dados" para o próprio SGBD, e não apenas para a aplicação.

## Erros comuns

* Esquecer o `NOT NULL` em colunas obrigatórias, permitindo cadastros incompletos.
* Não usar `FOREIGN KEY`, permitindo que uma matrícula referencie um aluno que não existe.
* Confundir `UNIQUE` com `PRIMARY KEY` (uma tabela pode ter várias colunas `UNIQUE`, mas apenas **uma** `PRIMARY KEY`).

## Resumo

Constraints (`PRIMARY KEY`, `FOREIGN KEY`, `NOT NULL`, `UNIQUE`, `DEFAULT`, `CHECK`) são regras que garantem a integridade dos dados diretamente no banco de dados.

---

# 13. INSERT (DML)

## O que é

O comando `INSERT INTO` adiciona novos registros (linhas) a uma tabela.

## Para que serve

Serve para cadastrar dados novos: um novo aluno, um novo curso, um novo pedido etc.

## Como funciona

### Inserindo um registro especificando as colunas

```sql
INSERT INTO aluno (id_aluno, nome, data_nascimento, email)
VALUES (1, 'Maria Silva', '2008-05-14', 'maria@email.com');
```

### Inserindo vários registros de uma vez

```sql
INSERT INTO aluno (id_aluno, nome, data_nascimento, email)
VALUES
    (2, 'João Souza', '2007-11-02', 'joao@email.com'),
    (3, 'Ana Costa', '2008-01-30', 'ana@email.com');
```

### Inserindo sem especificar as colunas

Se você informar os valores **na mesma ordem** das colunas da tabela, não precisa listá-las — mas isso é **arriscado**, porque qualquer mudança na estrutura da tabela pode quebrar o comando.

```sql
INSERT INTO curso VALUES (1, 'Desenvolvimento de Sistemas', 1200);
```

> **Boa prática:** sempre especifique as colunas explicitamente, mesmo que dê mais trabalho. Isso deixa o comando mais claro e seguro.

## Erros comuns

* Não especificar as colunas e inserir os valores fora de ordem, gerando dados errados.
* Esquecer de informar um campo `NOT NULL`, o que gera erro.
* Tentar inserir um valor de chave estrangeira que não existe na tabela referenciada (viola a integridade referencial).
* Inserir texto sem aspas simples (`'texto'`), o que gera erro de sintaxe.

## Resumo

`INSERT INTO tabela (colunas) VALUES (valores)` insere novos registros. É sempre recomendável especificar as colunas explicitamente.

---

# 14. SELECT (DQL)

## O que é

O comando `SELECT` é usado para **consultar** dados armazenados em uma ou mais tabelas. É, provavelmente, o comando mais usado em SQL.

## Estrutura básica

```sql
SELECT colunas
FROM tabela
WHERE condição;
```

## Selecionando todas as colunas

```sql
SELECT * FROM aluno;
```

O `*` significa "todas as colunas". É útil para explorar rapidamente uma tabela, mas em sistemas reais é recomendável selecionar apenas as colunas necessárias (por questão de desempenho e clareza).

## Selecionando colunas específicas

```sql
SELECT nome, email FROM aluno;
```

## Aliases com AS

`AS` renomeia uma coluna (ou tabela) no resultado da consulta, sem alterar o nome real no banco.

```sql
SELECT nome AS nome_do_aluno, email AS contato
FROM aluno;
```

## DISTINCT

Remove valores **duplicados** do resultado.

```sql
SELECT DISTINCT id_curso FROM aluno;
```

Isso retorna cada `id_curso` apenas uma vez, mesmo que vários alunos estejam no mesmo curso.

## Erros comuns

* Usar `SELECT *` em sistemas grandes sem necessidade, prejudicando o desempenho.
* Esquecer que `DISTINCT` se aplica à **combinação de todas as colunas selecionadas**, não a cada coluna isoladamente.
* Confundir `AS` (que é só um apelido de exibição) com uma alteração real na tabela.

## Resumo

`SELECT` consulta dados de uma tabela. Pode-se selecionar todas as colunas (`*`) ou colunas específicas, usar `AS` para apelidos e `DISTINCT` para remover duplicados.

---

# 15. Filtros e Operadores (WHERE)

## O que é

A cláusula `WHERE` filtra os registros retornados por um `SELECT` (ou afetados por um `UPDATE`/`DELETE`), com base em uma condição.

```sql
SELECT * FROM aluno WHERE id_curso = 1;
```

## Operadores de comparação

| Operador | Significado | Exemplo |
|---|---|---|
| `=` | Igual | `WHERE idade = 17` |
| `<>` ou `!=` | Diferente | `WHERE idade <> 17` |
| `>` | Maior que | `WHERE idade > 17` |
| `<` | Menor que | `WHERE idade < 17` |
| `>=` | Maior ou igual | `WHERE idade >= 18` |
| `<=` | Menor ou igual | `WHERE idade <= 18` |

> `<>` e `!=` significam a mesma coisa ("diferente"); `<>` é o padrão SQL, mas `!=` também funciona no MySQL.

## Operadores lógicos

| Operador | Significado | Exemplo |
|---|---|---|
| `AND` | E — todas as condições devem ser verdadeiras | `WHERE idade >= 15 AND idade <= 18` |
| `OR` | OU — pelo menos uma condição deve ser verdadeira | `WHERE id_curso = 1 OR id_curso = 2` |
| `NOT` | Nega a condição | `WHERE NOT id_curso = 1` |

## BETWEEN

Verifica se um valor está dentro de um intervalo (inclusive nos limites).

```sql
SELECT * FROM aluno WHERE idade BETWEEN 15 AND 18;
```

## IN

Verifica se um valor está dentro de uma lista de valores.

```sql
SELECT * FROM aluno WHERE id_curso IN (1, 2, 3);
```

## LIKE e os curingas

`LIKE` é usado para buscas de texto que seguem um padrão, geralmente combinado com os curingas:

* `%` → representa **zero ou mais caracteres** quaisquer.
* `_` → representa **exatamente um caractere** qualquer.

```sql
-- Nomes que começam com "Ma"
SELECT * FROM aluno WHERE nome LIKE 'Ma%';

-- Nomes que terminam com "Silva"
SELECT * FROM aluno WHERE nome LIKE '%Silva';

-- Nomes que contêm "os" em qualquer posição
SELECT * FROM aluno WHERE nome LIKE '%os%';

-- Nomes com exatamente 5 letras
SELECT * FROM aluno WHERE nome LIKE '_____';
```

## IS NULL e IS NOT NULL

Verifica se um campo está (ou não está) vazio/nulo. **Não se usa `= NULL`**, pois `NULL` representa "ausência de valor" e não pode ser comparado com `=`.

```sql
SELECT * FROM aluno WHERE email IS NULL;
SELECT * FROM aluno WHERE email IS NOT NULL;
```

## Erros comuns

* Usar `= NULL` em vez de `IS NULL` (isso nunca retorna resultados, pois `NULL` não é "igual" a nada).
* Confundir `%` com `_` no `LIKE`.
* Esquecer parênteses ao combinar `AND` e `OR`, o que pode alterar o resultado esperado.

```sql
-- Ambíguo / pode dar resultado inesperado:
SELECT * FROM aluno WHERE id_curso = 1 OR id_curso = 2 AND idade > 16;

-- Mais claro, usando parênteses:
SELECT * FROM aluno WHERE (id_curso = 1 OR id_curso = 2) AND idade > 16;
```

## Resumo

`WHERE` filtra registros usando operadores de comparação, lógicos, `BETWEEN`, `IN`, `LIKE` (com `%` e `_`) e `IS NULL`/`IS NOT NULL`.

---

# 16. ORDER BY

## O que é

`ORDER BY` ordena o resultado de uma consulta com base em uma ou mais colunas.

```sql
SELECT * FROM aluno ORDER BY nome;
```

## ASC e DESC

* `ASC` → ordem crescente (é o padrão, pode ser omitido).
* `DESC` → ordem decrescente.

```sql
-- Do mais novo para o mais velho
SELECT * FROM aluno ORDER BY data_nascimento DESC;

-- Por nome (A-Z) e, em caso de empate, por idade (do menor para o maior)
SELECT * FROM aluno ORDER BY nome ASC, idade ASC;
```

## Erros comuns

* Esquecer que, sem `ORDER BY`, a ordem dos resultados **não é garantida**.
* Achar que `DESC` se aplica a todas as colunas listadas — na verdade, é preciso repetir `DESC` para cada coluna que deve ser decrescente.

## Resumo

`ORDER BY coluna ASC|DESC` ordena os resultados de uma consulta, podendo combinar várias colunas.

---

# 17. LIMIT

## O que é

`LIMIT` restringe a **quantidade de linhas** retornadas por uma consulta.

```sql
-- Retorna apenas os 5 primeiros registros
SELECT * FROM aluno LIMIT 5;
```

## Combinando com OFFSET

`OFFSET` pula um número de registros antes de começar a retornar (útil para paginação).

```sql
-- Pula os 5 primeiros e retorna os próximos 5
SELECT * FROM aluno LIMIT 5 OFFSET 5;
```

## Diferenças entre SGBDs

* **MySQL/MariaDB/PostgreSQL/SQLite**: usam `LIMIT` (e `OFFSET`).
* **SQL Server**: não usa `LIMIT`; usa `TOP` (`SELECT TOP 5 * FROM aluno;`) ou `OFFSET ... FETCH`.
* **Oracle** (versões mais recentes): usa `FETCH FIRST n ROWS ONLY`.

## Resumo

`LIMIT n` limita a quantidade de linhas retornadas; combinado com `OFFSET`, permite paginação. A sintaxe varia entre SGBDs.

---

# 18. UPDATE

## O que é

`UPDATE` altera valores de registros já existentes em uma tabela.

## Como funciona

```sql
UPDATE tabela
SET coluna1 = valor1, coluna2 = valor2
WHERE condição;
```

## Exemplo seguro

```sql
UPDATE aluno
SET email = 'novoemail@email.com'
WHERE id_aluno = 1;
```

## ⚠️ O perigo de esquecer o WHERE

Se o `WHERE` for esquecido, o `UPDATE` **altera todos os registros da tabela**, o que quase sempre é um erro grave.

```sql
-- PERIGOSO: atualiza o e-mail de TODOS os alunos!
UPDATE aluno
SET email = 'novoemail@email.com';
```

> **Boa prática:** antes de rodar um `UPDATE`, rode um `SELECT` com a mesma condição do `WHERE` para conferir exatamente quais registros serão alterados.

```sql
-- 1º: conferir quem será afetado
SELECT * FROM aluno WHERE id_aluno = 1;

-- 2º: só então rodar o UPDATE
UPDATE aluno SET email = 'novoemail@email.com' WHERE id_aluno = 1;
```

## Erros comuns

* Esquecer o `WHERE` (o erro mais perigoso de todo o SQL).
* Atualizar a coluna errada por erro de digitação.
* Esquecer aspas simples em valores de texto.

## Resumo

`UPDATE tabela SET coluna = valor WHERE condição` altera registros existentes. Esquecer o `WHERE` altera **todos** os registros da tabela — é um dos erros mais perigosos em SQL.

---

# 19. DELETE, DROP e TRUNCATE

## DELETE

Remove **registros** (linhas) de uma tabela, mantendo a estrutura da tabela.

```sql
DELETE FROM aluno WHERE id_aluno = 3;
```

### ⚠️ O perigo de esquecer o WHERE

Assim como no `UPDATE`, esquecer o `WHERE` no `DELETE` remove **todos os registros** da tabela.

```sql
-- PERIGOSO: apaga TODOS os alunos!
DELETE FROM aluno;
```

## Diferença entre DELETE, DROP e TRUNCATE

| Comando | O que faz | Remove a estrutura? | Pode usar WHERE? | Categoria |
|---|---|---|---|---|
| `DELETE` | Remove registros específicos | Não | Sim | DML |
| `TRUNCATE` | Remove **todos** os registros de uma vez, de forma mais rápida | Não | Não | DDL |
| `DROP` | Remove a **tabela inteira** (estrutura + dados) | Sim | Não | DDL |

```sql
-- Remove alunos específicos
DELETE FROM aluno WHERE id_curso = 5;

-- Remove todos os registros da tabela, mas mantém a tabela vazia
TRUNCATE TABLE aluno;

-- Remove a tabela inteira do banco de dados
DROP TABLE aluno;
```

## Erros comuns

* Esquecer o `WHERE` no `DELETE`.
* Confundir `DELETE FROM tabela` (apaga os dados) com `DROP TABLE` (apaga a tabela inteira, incluindo a estrutura).
* Usar `TRUNCATE` sem perceber que ele não pode ser filtrado com `WHERE`.

## Resumo

`DELETE` remove registros específicos (pode usar `WHERE`); `TRUNCATE` remove todos os registros de uma vez; `DROP` remove a tabela inteira, incluindo sua estrutura.

---

# 20. ALTER TABLE

## O que é

`ALTER TABLE` modifica a estrutura de uma tabela já existente (sem precisar recriá-la).

## Adicionar coluna

```sql
ALTER TABLE aluno ADD COLUMN telefone VARCHAR(20);
```

## Modificar coluna

```sql
-- MySQL/MariaDB
ALTER TABLE aluno MODIFY COLUMN telefone VARCHAR(30);
```

## Remover coluna

```sql
ALTER TABLE aluno DROP COLUMN telefone;
```

## Adicionar constraint

```sql
ALTER TABLE aluno ADD CONSTRAINT fk_curso
FOREIGN KEY (id_curso) REFERENCES curso(id_curso);
```

## Diferenças entre SGBDs

A sintaxe do `ALTER TABLE` pode variar bastante:

* **MySQL/MariaDB**: usa `MODIFY COLUMN` para alterar uma coluna.
* **PostgreSQL/SQL Server**: usam `ALTER COLUMN` em vez de `MODIFY COLUMN`.

Por isso, ao estudar por outras fontes, é importante verificar qual SGBD está sendo usado nos exemplos.

## Erros comuns

* Tentar remover uma coluna que é referenciada por uma `FOREIGN KEY` sem antes remover essa dependência.
* Usar a sintaxe de um SGBD em outro (ex.: `MODIFY COLUMN` no PostgreSQL, que não é aceito).

## Resumo

`ALTER TABLE` permite adicionar, modificar ou remover colunas e constraints em uma tabela já existente, com sintaxe que pode variar entre SGBDs.

---

# 21. Funções de Agregação

## O que são

Funções de agregação realizam **cálculos** sobre um conjunto de linhas e retornam um único valor (um resumo).

## Principais funções

| Função | O que faz | Exemplo |
|---|---|---|
| `COUNT()` | Conta o número de linhas | `COUNT(*)` |
| `SUM()` | Soma os valores de uma coluna numérica | `SUM(nota)` |
| `AVG()` | Calcula a média dos valores | `AVG(nota)` |
| `MIN()` | Retorna o menor valor | `MIN(nota)` |
| `MAX()` | Retorna o maior valor | `MAX(nota)` |

## Exemplos

```sql
-- Quantos alunos existem no total?
SELECT COUNT(*) FROM aluno;

-- Qual é a média das notas?
SELECT AVG(nota) FROM matricula;

-- Qual é a nota mais alta e a mais baixa?
SELECT MAX(nota) AS maior_nota, MIN(nota) AS menor_nota FROM matricula;

-- Soma da carga horária de todos os cursos
SELECT SUM(carga_horaria) FROM curso;
```

## Erros comuns

* Usar `COUNT(coluna)` achando que é igual a `COUNT(*)` — na verdade, `COUNT(coluna)` ignora valores `NULL` daquela coluna, enquanto `COUNT(*)` conta todas as linhas.
* Tentar usar `SUM`/`AVG` em colunas de texto.
* Esquecer que funções de agregação, sozinhas, resumem **toda** a tabela — para resumir por grupos, é necessário `GROUP BY` (próxima seção).

## Resumo

Funções de agregação (`COUNT`, `SUM`, `AVG`, `MIN`, `MAX`) calculam um valor resumo a partir de várias linhas.

---

# 22. GROUP BY

## O que é

`GROUP BY` agrupa linhas que têm o mesmo valor em uma (ou mais) coluna, permitindo aplicar funções de agregação **para cada grupo** separadamente.

## Exemplo progressivo

### Sem GROUP BY (agregação da tabela inteira)

```sql
SELECT AVG(nota) FROM matricula;
```

Retorna **uma única média**, considerando todos os alunos e cursos juntos.

### Com GROUP BY (agregação por grupo)

```sql
SELECT id_curso, AVG(nota) AS media_curso
FROM matricula
GROUP BY id_curso;
```

Agora, retorna **uma média para cada curso** — um grupo por `id_curso`.

### Outro exemplo — contando alunos por curso

```sql
SELECT id_curso, COUNT(*) AS total_alunos
FROM aluno
GROUP BY id_curso;
```

## Regra importante

Toda coluna que aparece no `SELECT` **sem** estar dentro de uma função de agregação deve também aparecer no `GROUP BY`.

```sql
-- Correto:
SELECT id_curso, COUNT(*) FROM aluno GROUP BY id_curso;

-- Errado (nome não está agregado nem no GROUP BY):
SELECT id_curso, nome, COUNT(*) FROM aluno GROUP BY id_curso;
```

## Erros comuns

* Colocar no `SELECT` uma coluna que não está nem agregada nem no `GROUP BY`.
* Confundir `GROUP BY` com `ORDER BY` (o `GROUP BY` **agrupa** linhas para agregação; o `ORDER BY` apenas **ordena** o resultado final).

## Resumo

`GROUP BY coluna` agrupa os registros pela coluna informada, permitindo calcular agregações (como `COUNT`, `AVG`) separadamente para cada grupo.

---

# 23. HAVING

## Diferença entre WHERE e HAVING

Este é um dos pontos que mais gera confusão em BD1. A diferença fundamental é:

| Cláusula | Filtra o quê | Quando age | Pode usar função de agregação? |
|---|---|---|---|
| `WHERE` | Linhas **individuais**, antes de agrupar | Antes do `GROUP BY` | **Não** |
| `HAVING` | **Grupos** já formados pelo `GROUP BY` | Depois do `GROUP BY` | **Sim** |

## Por que isso acontece

O `WHERE` é processado **antes** de os dados serem agrupados — por isso ele não "enxerga" o resultado de uma função de agregação, que só existe depois do agrupamento. Já o `HAVING` age **depois** do agrupamento, podendo filtrar com base em `COUNT`, `AVG`, `SUM` etc.

## Exemplo — usando WHERE (filtra linhas antes de agrupar)

```sql
-- Só considera matrículas do ano de 2024 antes de calcular a média por curso
SELECT id_curso, AVG(nota) AS media
FROM matricula
WHERE YEAR(data_matricula) = 2024
GROUP BY id_curso;
```

## Exemplo — usando HAVING (filtra depois de agrupar)

```sql
-- Mostra apenas os cursos cuja média de notas é maior que 7
SELECT id_curso, AVG(nota) AS media
FROM matricula
GROUP BY id_curso
HAVING AVG(nota) > 7;
```

## Exemplo combinando WHERE e HAVING

```sql
SELECT id_curso, AVG(nota) AS media
FROM matricula
WHERE status = 'ativa'
GROUP BY id_curso
HAVING AVG(nota) > 7;
```

Aqui: o `WHERE` filtra **antes** de agrupar (só matrículas ativas), e o `HAVING` filtra **depois** de agrupar (só cursos com média acima de 7).

## Ordem lógica de execução (simplificada)

```
FROM → WHERE → GROUP BY → HAVING → SELECT → ORDER BY → LIMIT
```

## Erros comuns

* Tentar usar uma função de agregação dentro do `WHERE` (ex.: `WHERE AVG(nota) > 7`) — isso gera **erro**, pois o `WHERE` age antes de haver qualquer agregação.
* Usar `HAVING` para filtrar uma condição simples que não envolve agregação (nesse caso, `WHERE` é mais eficiente e é o correto a se usar).

## Resumo

`WHERE` filtra linhas antes do agrupamento e **não aceita** funções de agregação; `HAVING` filtra grupos depois do `GROUP BY` e **aceita** funções de agregação.

---

# 24. JOIN

## O que é

`JOIN` combina linhas de duas (ou mais) tabelas com base em uma condição de relacionamento, geralmente entre uma chave primária e uma chave estrangeira.

## Tabelas de exemplo para esta seção

**alunos**

| id_aluno | nome | id_curso |
|---|---|---|
| 1 | Maria | 10 |
| 2 | João | 10 |
| 3 | Ana | NULL |

**cursos**

| id_curso | nome_curso |
|---|---|
| 10 | Desenvolvimento de Sistemas |
| 20 | Administração |

**matriculas**

| id_aluno | id_curso | nota |
|---|---|---|
| 1 | 10 | 8.5 |
| 2 | 10 | 7.0 |

## INNER JOIN

Retorna **apenas** as linhas em que existe correspondência **nas duas** tabelas.

```sql
SELECT alunos.nome, cursos.nome_curso
FROM alunos
INNER JOIN cursos ON alunos.id_curso = cursos.id_curso;
```

**Resultado:** apenas Maria e João aparecem (ambos têm `id_curso` preenchido e correspondente). Ana **não aparece**, pois seu `id_curso` é `NULL` e o curso "Administração" também não aparece, pois nenhum aluno está matriculado nele.

## LEFT JOIN

Retorna **todas** as linhas da tabela da **esquerda** (a primeira tabela, mencionada no `FROM`), mesmo que não haja correspondência na tabela da direita. Quando não há correspondência, os campos da tabela da direita vêm como `NULL`.

```sql
SELECT alunos.nome, cursos.nome_curso
FROM alunos
LEFT JOIN cursos ON alunos.id_curso = cursos.id_curso;
```

**Resultado:** Maria, João **e Ana** aparecem. Para Ana, `nome_curso` aparece como `NULL`, pois ela não está matriculada em nenhum curso.

## RIGHT JOIN

É o "espelho" do `LEFT JOIN`: retorna **todas** as linhas da tabela da **direita**, mesmo sem correspondência na tabela da esquerda.

```sql
SELECT alunos.nome, cursos.nome_curso
FROM alunos
RIGHT JOIN cursos ON alunos.id_curso = cursos.id_curso;
```

**Resultado:** Maria, João **e também o curso "Administração"** (mesmo sem nenhum aluno matriculado, aparecerá com `nome = NULL`).

## FULL OUTER JOIN

Retorna **todas** as linhas de ambas as tabelas, combinando o comportamento do `LEFT JOIN` e do `RIGHT JOIN`. Linhas sem correspondência de um dos lados aparecem com `NULL` no outro lado.

```sql
SELECT alunos.nome, cursos.nome_curso
FROM alunos
FULL OUTER JOIN cursos ON alunos.id_curso = cursos.id_curso;
```

> **Atenção:** o **MySQL/MariaDB não possui `FULL OUTER JOIN` nativamente**. Para simular esse comportamento, combina-se um `LEFT JOIN` e um `RIGHT JOIN` com `UNION`:
>
> ```sql
> SELECT alunos.nome, cursos.nome_curso
> FROM alunos LEFT JOIN cursos ON alunos.id_curso = cursos.id_curso
> UNION
> SELECT alunos.nome, cursos.nome_curso
> FROM alunos RIGHT JOIN cursos ON alunos.id_curso = cursos.id_curso;
> ```

## Resumo visual do que cada JOIN retorna

| JOIN | O que retorna |
|---|---|
| `INNER JOIN` | Somente as linhas com correspondência nas duas tabelas |
| `LEFT JOIN` | Todas as linhas da esquerda + correspondências da direita (ou NULL) |
| `RIGHT JOIN` | Todas as linhas da direita + correspondências da esquerda (ou NULL) |
| `FULL OUTER JOIN` | Todas as linhas de ambas as tabelas, com NULL onde não houver correspondência |

## JOIN vs. várias tabelas no FROM (sem JOIN explícito)

É possível "juntar" tabelas listando-as no `FROM` separadas por vírgula, mas isso é uma prática **desatualizada e arriscada**:

```sql
-- Estilo antigo, evite:
SELECT alunos.nome, cursos.nome_curso
FROM alunos, cursos
WHERE alunos.id_curso = cursos.id_curso;
```

Esse estilo é equivalente a um `INNER JOIN`, mas:

* É mais fácil esquecer a condição no `WHERE`, gerando um **produto cartesiano** (combinação de TODAS as linhas de uma tabela com TODAS as linhas da outra, o que gera resultados absurdos e incorretos).
* Não deixa claro, visualmente, qual é a condição de relacionamento.
* Não permite `LEFT JOIN`/`RIGHT JOIN` de forma direta.

**Por isso, sempre prefira a sintaxe explícita com `JOIN ... ON ...`.**

## Erros comuns

* Esquecer a condição `ON`, gerando um produto cartesiano.
* Confundir `INNER JOIN` (só o que casa) com `LEFT JOIN` (tudo da esquerda, casando ou não).
* Usar vírgula no `FROM` em vez de `JOIN` explícito.

## Resumo

`JOIN` combina tabelas relacionadas. `INNER JOIN` traz só as correspondências; `LEFT`/`RIGHT JOIN` trazem todas as linhas de um dos lados, mesmo sem correspondência; `FULL OUTER JOIN` traz tudo dos dois lados (não suportado nativamente pelo MySQL).

---

# 25. Subconsultas

## O que é

Uma **subconsulta** (ou *subquery*) é um `SELECT` colocado dentro de outro comando SQL (geralmente dentro de outro `SELECT`, mas também pode estar dentro de `INSERT`, `UPDATE` ou `DELETE`).

## Para que serve

Serve para usar o resultado de uma consulta como base para outra consulta, quando não é possível (ou não é prático) resolver tudo em um único passo.

## Exemplo 1 — subconsulta no WHERE

```sql
-- Alunos que estão matriculados no curso "Desenvolvimento de Sistemas"
SELECT nome
FROM aluno
WHERE id_curso = (
    SELECT id_curso FROM curso WHERE nome_curso = 'Desenvolvimento de Sistemas'
);
```

## Exemplo 2 — subconsulta com IN

```sql
-- Alunos que têm nota maior que 8 em alguma matrícula
SELECT nome
FROM aluno
WHERE id_aluno IN (
    SELECT id_aluno FROM matricula WHERE nota > 8
);
```

## Exemplo 3 — subconsulta no FROM

```sql
-- Média de notas por curso, filtrando só cursos com média acima de 7
SELECT * FROM (
    SELECT id_curso, AVG(nota) AS media
    FROM matricula
    GROUP BY id_curso
) AS medias
WHERE media > 7;
```

## Erros comuns

* Esquecer que uma subconsulta que retorna **mais de um valor** não pode ser usada com `=` (deve-se usar `IN`).
* Não colocar a subconsulta entre parênteses.
* Criar subconsultas desnecessariamente complexas quando um `JOIN` resolveria de forma mais simples e eficiente.

## Resumo

Uma subconsulta é um `SELECT` dentro de outro comando, usada para resolver consultas em etapas, no `WHERE`, `IN` ou até no `FROM`.

---

# 26. Relacionamentos em SQL

Retomando a seção 6, agora com foco totalmente prático em como implementar cada tipo de relacionamento.

## 1:1 em SQL

A FK fica em uma das tabelas, com `UNIQUE`, garantindo que não haja mais de uma relação.

```sql
CREATE TABLE professor (
    id_professor INT PRIMARY KEY,
    nome VARCHAR(100)
);

CREATE TABLE sala (
    id_sala INT PRIMARY KEY,
    numero VARCHAR(10),
    id_professor INT UNIQUE,
    FOREIGN KEY (id_professor) REFERENCES professor(id_professor)
);
```

## 1:N em SQL

A FK sempre fica no lado "muitos".

```sql
CREATE TABLE curso (
    id_curso INT PRIMARY KEY,
    nome_curso VARCHAR(100)
);

CREATE TABLE aluno (
    id_aluno INT PRIMARY KEY,
    nome VARCHAR(100),
    id_curso INT,
    FOREIGN KEY (id_curso) REFERENCES curso(id_curso)
);
```

## N:N em SQL

Sempre exige uma tabela intermediária (associativa), com as duas FKs formando (geralmente) a chave composta.

```sql
CREATE TABLE aluno (
    id_aluno INT PRIMARY KEY,
    nome VARCHAR(100)
);

CREATE TABLE disciplina (
    id_disciplina INT PRIMARY KEY,
    nome_disciplina VARCHAR(100)
);

CREATE TABLE aluno_disciplina (
    id_aluno INT,
    id_disciplina INT,
    PRIMARY KEY (id_aluno, id_disciplina),
    FOREIGN KEY (id_aluno) REFERENCES aluno(id_aluno),
    FOREIGN KEY (id_disciplina) REFERENCES disciplina(id_disciplina)
);
```

## Onde colocar a FK — resumo rápido

| Relacionamento | Onde fica a FK |
|---|---|
| 1:1 | Em uma das tabelas (com `UNIQUE`) |
| 1:N | Na tabela do lado "N" (muitos) |
| N:N | Em uma tabela intermediária nova |

## Resumo

Implementar relacionamentos em SQL depende do tipo: 1:1 usa FK com `UNIQUE`; 1:N coloca a FK no lado "muitos"; N:N sempre precisa de uma tabela associativa.

---

# 27. Integridade dos Dados

## O que é

**Integridade dos dados** é o conjunto de regras que garantem que os dados armazenados no banco sejam **corretos, consistentes e confiáveis**.

## Integridade de entidade

Garante que cada tabela tenha uma **chave primária válida** — ou seja, única e não nula. Isso assegura que cada registro possa ser identificado sem ambiguidade.

> Exemplo: não pode existir duas linhas com o mesmo `id_aluno`, nem uma linha com `id_aluno` vazio.

## Integridade referencial

Garante que os valores de uma **chave estrangeira** sempre correspondam a um valor existente na tabela referenciada (ou sejam nulos, se permitido).

> Exemplo: não pode existir uma `matricula` com `id_curso = 99` se não existir nenhum curso com `id_curso = 99`.

```sql
-- Isso geraria erro de integridade referencial, se o curso 99 não existir:
INSERT INTO matricula (id_aluno, id_curso, data_matricula)
VALUES (1, 99, '2024-02-01');
```

## Integridade de domínio

Garante que os valores inseridos em uma coluna respeitem o **tipo de dado** e as **restrições** definidas (como `CHECK`, tamanho máximo, etc.).

> Exemplo: não pode existir uma `nota` com valor `"abc"` em uma coluna `DECIMAL`, nem uma nota `15` se houver um `CHECK (nota <= 10)`.

## Resumo comparativo

| Tipo de integridade | O que garante | Exemplo de violação |
|---|---|---|
| De entidade | PK única e não nula | Dois alunos com o mesmo `id_aluno` |
| Referencial | FK aponta para valor existente | Matrícula com `id_curso` inexistente |
| De domínio | Valores respeitam tipo/regras | Nota com valor de texto ou fora do intervalo |

## Erros comuns

* Desativar as constraints "para facilitar" o desenvolvimento e esquecer de reativá-las.
* Confiar apenas na aplicação (código) para validar os dados, sem constraints no banco.

## Resumo

A integridade dos dados garante confiabilidade no banco através de três pilares: integridade de entidade (PK), integridade referencial (FK) e integridade de domínio (tipos/regras dos valores).

---

# 28. Transações

## O que é uma transação

Uma **transação** é um conjunto de operações SQL (como vários `INSERT`, `UPDATE`, `DELETE`) tratado como **uma única unidade** — ou tudo é executado com sucesso, ou nada é aplicado.

> Exemplo clássico: uma transferência bancária envolve **debitar** de uma conta e **creditar** em outra. Essas duas operações devem acontecer juntas — se uma falhar, a outra também deve ser desfeita.

## COMMIT e ROLLBACK

* **`COMMIT`**: confirma definitivamente todas as alterações feitas na transação, salvando-as no banco.
* **`ROLLBACK`**: desfaz todas as alterações feitas desde o início da transação, como se nada tivesse acontecido.

```sql
START TRANSACTION;

UPDATE conta SET saldo = saldo - 100 WHERE id_conta = 1;
UPDATE conta SET saldo = saldo + 100 WHERE id_conta = 2;

-- Se tudo ocorreu certo:
COMMIT;

-- Se algo deu errado:
-- ROLLBACK;
```

## O conceito de ACID (introdução)

**ACID** é o conjunto de propriedades que uma transação confiável deve ter:

| Propriedade | Significado |
|---|---|
| **A**tomicidade | A transação é "tudo ou nada" — não existe execução parcial |
| **C**onsistência | A transação leva o banco de um estado válido para outro estado válido, respeitando todas as regras |
| **I**solamento | Transações executadas ao mesmo tempo não interferem umas nas outras |
| **D**urabilidade | Uma vez confirmada (`COMMIT`), a alteração é permanente, mesmo em caso de falha do sistema |

> Para BD1, o importante é entender **o que cada letra significa de forma geral** — um estudo aprofundado de controle de concorrência e isolamento fica para módulos mais avançados de banco de dados.

## Erros comuns

* Esquecer o `COMMIT`, fazendo com que as alterações não sejam salvas de forma permanente (dependendo da configuração do SGBD).
* Confundir `ROLLBACK` com `DELETE` (o `ROLLBACK` desfaz uma transação inteira; o `DELETE` remove dados especificamente).

## Resumo

Uma transação agrupa várias operações como uma unidade só; `COMMIT` confirma as alterações, `ROLLBACK` as desfaz. O conceito de ACID resume as propriedades que garantem a confiabilidade de uma transação.

---

# 29. Índices

## O que é um índice

Um **índice** é uma estrutura auxiliar que o SGBD cria para **acelerar** a busca de registros em uma tabela, de forma parecida com o índice de um livro, que permite encontrar um assunto sem precisar ler todas as páginas.

## Para que serve

Serve para tornar consultas (`SELECT` com `WHERE`, `JOIN`, `ORDER BY`) mais rápidas, especialmente em tabelas grandes.

## Como funciona (visão simples)

Sem índice, o SGBD normalmente precisa percorrer **linha por linha** da tabela até encontrar o que procura (chamado de *table scan*). Com um índice, o SGBD consegue "pular" diretamente para os registros relevantes, de forma parecida com uma busca binária.

```sql
CREATE INDEX idx_nome_aluno ON aluno (nome);
```

Toda `PRIMARY KEY` já cria automaticamente um índice. É comum também criar índices em colunas usadas com frequência em `WHERE` e `JOIN`, como chaves estrangeiras.

## Vantagens

* Acelera muito consultas de busca e ordenação.
* Melhora o desempenho de `JOIN`s entre tabelas grandes.

## Desvantagens

* Ocupa espaço extra em disco.
* **Deixa `INSERT`, `UPDATE` e `DELETE` um pouco mais lentos**, pois o índice também precisa ser atualizado a cada alteração.
* Criar índices demais, sem necessidade, pode prejudicar o desempenho geral em vez de ajudar.

## Relação entre índice e desempenho

* **Leitura (SELECT)**: geralmente melhora bastante com índices bem escolhidos.
* **Escrita (INSERT/UPDATE/DELETE)**: geralmente piora um pouco, pois o índice precisa ser recalculado.

Por isso, a criação de índices é sempre um **equilíbrio**: colocar índices nas colunas mais consultadas, sem exagerar.

## Erros comuns

* Achar que "quanto mais índices, melhor" — na prática, índices em excesso prejudicam a escrita.
* Esquecer de indexar colunas usadas com frequência em `JOIN` e `WHERE`, deixando o sistema lento.

## Resumo

Um índice acelera buscas, funcionando como um "atalho" para encontrar registros. Melhora a leitura, mas tem um custo na escrita e no espaço em disco, exigindo equilíbrio na hora de criá-los.

---

# 30. Projeto Completo — Sistema Escolar

Vamos aplicar tudo o que foi estudado em um projeto completo de banco de dados para uma escola.

## Passo 1 — Levantamento dos requisitos

A escola precisa controlar:

* Alunos matriculados;
* Professores;
* Cursos oferecidos;
* Disciplinas de cada curso;
* Turmas;
* Matrículas dos alunos nas turmas;
* Notas dos alunos em cada disciplina.

## Passo 2 — Identificação das entidades

`Aluno`, `Professor`, `Curso`, `Disciplina`, `Turma`, `Matricula`, `Nota`.

## Passo 3 — Identificação dos atributos

| Entidade | Atributos |
|---|---|
| Aluno | id_aluno, nome, data_nascimento, email |
| Professor | id_professor, nome, email |
| Curso | id_curso, nome_curso, carga_horaria |
| Disciplina | id_disciplina, nome_disciplina, id_curso |
| Turma | id_turma, id_disciplina, id_professor, ano, semestre |
| Matricula | id_aluno, id_turma, data_matricula |
| Nota | id_matricula, valor_nota, tipo_avaliacao |

## Passo 4 — Identificação das chaves

* `Aluno`: PK = `id_aluno`
* `Professor`: PK = `id_professor`
* `Curso`: PK = `id_curso`
* `Disciplina`: PK = `id_disciplina`; FK = `id_curso`
* `Turma`: PK = `id_turma`; FKs = `id_disciplina`, `id_professor`
* `Matricula`: PK = `id_matricula`; FKs = `id_aluno`, `id_turma`
* `Nota`: PK = `id_nota`; FK = `id_matricula`

## Passo 5 — Relacionamentos

* `Curso` 1:N `Disciplina` (um curso tem várias disciplinas)
* `Disciplina` 1:N `Turma` (uma disciplina pode ter várias turmas, ex.: em anos diferentes)
* `Professor` 1:N `Turma` (um professor leciona várias turmas)
* `Aluno` N:N `Turma`, resolvido pela tabela `Matricula`
* `Matricula` 1:N `Nota` (uma matrícula pode ter várias notas — provas, trabalhos etc.)

## Passo 6 — Cardinalidades

| Relacionamento | Cardinalidade |
|---|---|
| Curso — Disciplina | (1,N) |
| Disciplina — Turma | (0,N) |
| Professor — Turma | (0,N) |
| Aluno — Matricula | (0,N) |
| Turma — Matricula | (0,N) |
| Matricula — Nota | (0,N) |

## Passo 7 — Modelo Conceitual (DER textual)

```
[CURSO] --(1,N)-- possui --(1,1)-- [DISCIPLINA]
[DISCIPLINA] --(1,1)-- é oferecida em --(0,N)-- [TURMA]
[PROFESSOR] --(1,1)-- leciona --(0,N)-- [TURMA]
[ALUNO] --(0,N)-- se matricula --(0,N)-- [TURMA]   (via MATRICULA)
[MATRICULA] --(1,1)-- recebe --(0,N)-- [NOTA]
```

## Passo 8 — Modelo Lógico

```
curso(id_curso, nome_curso, carga_horaria)
disciplina(id_disciplina, nome_disciplina, id_curso*)
professor(id_professor, nome, email)
turma(id_turma, id_disciplina*, id_professor*, ano, semestre)
aluno(id_aluno, nome, data_nascimento, email)
matricula(id_matricula, id_aluno*, id_turma*, data_matricula)
nota(id_nota, id_matricula*, valor_nota, tipo_avaliacao)
```
*(`*` indica chave estrangeira)*

## Passo 9 e 10 — Tabelas e SQL de criação

```sql
CREATE DATABASE escola;
USE escola;

CREATE TABLE curso (
    id_curso INT PRIMARY KEY AUTO_INCREMENT,
    nome_curso VARCHAR(100) NOT NULL,
    carga_horaria INT
);

CREATE TABLE disciplina (
    id_disciplina INT PRIMARY KEY AUTO_INCREMENT,
    nome_disciplina VARCHAR(100) NOT NULL,
    id_curso INT NOT NULL,
    FOREIGN KEY (id_curso) REFERENCES curso(id_curso)
);

CREATE TABLE professor (
    id_professor INT PRIMARY KEY AUTO_INCREMENT,
    nome VARCHAR(100) NOT NULL,
    email VARCHAR(100) UNIQUE
);

CREATE TABLE turma (
    id_turma INT PRIMARY KEY AUTO_INCREMENT,
    id_disciplina INT NOT NULL,
    id_professor INT,
    ano INT NOT NULL,
    semestre INT NOT NULL,
    FOREIGN KEY (id_disciplina) REFERENCES disciplina(id_disciplina),
    FOREIGN KEY (id_professor) REFERENCES professor(id_professor)
);

CREATE TABLE aluno (
    id_aluno INT PRIMARY KEY AUTO_INCREMENT,
    nome VARCHAR(100) NOT NULL,
    data_nascimento DATE,
    email VARCHAR(100) UNIQUE
);

CREATE TABLE matricula (
    id_matricula INT PRIMARY KEY AUTO_INCREMENT,
    id_aluno INT NOT NULL,
    id_turma INT NOT NULL,
    data_matricula DATE NOT NULL,
    FOREIGN KEY (id_aluno) REFERENCES aluno(id_aluno),
    FOREIGN KEY (id_turma) REFERENCES turma(id_turma)
);

CREATE TABLE nota (
    id_nota INT PRIMARY KEY AUTO_INCREMENT,
    id_matricula INT NOT NULL,
    valor_nota DECIMAL(4,2) CHECK (valor_nota >= 0 AND valor_nota <= 10),
    tipo_avaliacao VARCHAR(50),
    FOREIGN KEY (id_matricula) REFERENCES matricula(id_matricula)
);
```

## Passo 11 — Inserção de dados

```sql
INSERT INTO curso (nome_curso, carga_horaria) VALUES
('Desenvolvimento de Sistemas', 1200),
('Administração', 800);

INSERT INTO disciplina (nome_disciplina, id_curso) VALUES
('Banco de Dados 1', 1),
('Programação Orientada a Objetos', 1),
('Gestão Empresarial', 2);

INSERT INTO professor (nome, email) VALUES
('Carlos Mendes', 'carlos@escola.com'),
('Fernanda Lima', 'fernanda@escola.com');

INSERT INTO turma (id_disciplina, id_professor, ano, semestre) VALUES
(1, 1, 2024, 1),
(2, 2, 2024, 1);

INSERT INTO aluno (nome, data_nascimento, email) VALUES
('Maria Silva', '2008-05-14', 'maria@email.com'),
('João Souza', '2007-11-02', 'joao@email.com'),
('Ana Costa', '2008-01-30', 'ana@email.com');

INSERT INTO matricula (id_aluno, id_turma, data_matricula) VALUES
(1, 1, '2024-02-01'),
(2, 1, '2024-02-01'),
(3, 2, '2024-02-01');

INSERT INTO nota (id_matricula, valor_nota, tipo_avaliacao) VALUES
(1, 8.5, 'Prova 1'),
(1, 9.0, 'Trabalho'),
(2, 6.0, 'Prova 1'),
(3, 7.5, 'Prova 1');
```

## Passo 12 — Consultas com SELECT

```sql
-- Todos os alunos
SELECT * FROM aluno;

-- Nome e e-mail dos alunos, ordenados por nome
SELECT nome, email FROM aluno ORDER BY nome;
```

## Passo 13 — Consultas com JOIN

```sql
-- Nome do aluno, disciplina e nota
SELECT aluno.nome AS aluno, disciplina.nome_disciplina AS disciplina, nota.valor_nota
FROM aluno
INNER JOIN matricula ON aluno.id_aluno = matricula.id_aluno
INNER JOIN turma ON matricula.id_turma = turma.id_turma
INNER JOIN disciplina ON turma.id_disciplina = disciplina.id_disciplina
INNER JOIN nota ON nota.id_matricula = matricula.id_matricula;
```

## Passo 14 — Consultas com GROUP BY

```sql
-- Quantos alunos há em cada turma
SELECT id_turma, COUNT(*) AS total_alunos
FROM matricula
GROUP BY id_turma;
```

## Passo 15 — Consultas com funções de agregação

```sql
-- Média de notas por matrícula (por aluno em uma turma específica)
SELECT id_matricula, AVG(valor_nota) AS media
FROM nota
GROUP BY id_matricula
HAVING AVG(valor_nota) >= 7;
```

## Resumo do projeto

Este projeto mostrou o caminho completo: do levantamento de requisitos até consultas avançadas com `JOIN`, `GROUP BY` e `HAVING`, reunindo praticamente todo o conteúdo estudado nesta apostila.

---

# 31. Exercícios para Praticar

*(Baseados nas tabelas do projeto escolar: `aluno`, `curso`, `disciplina`, `professor`, `turma`, `matricula`, `nota`)*

## Nível 1 — Fácil

1. O que é um SGBD? Cite dois exemplos.
2. Qual a diferença entre banco de dados e SGBD?
3. Escreva um `SELECT` que retorne todos os alunos.
4. Escreva um `SELECT` que retorne apenas o nome e o e-mail dos alunos.
5. O que faz a cláusula `DISTINCT`?
6. Escreva um comando que insira um novo curso chamado "Informática para Internet" com 1000 horas.
7. O que é uma chave primária?
8. O que é uma chave estrangeira?
9. Escreva um `SELECT` que retorne os alunos ordenados por nome, do A ao Z.
10. Escreva um `SELECT` que retorne apenas os 3 primeiros alunos cadastrados.

## Nível 2 — Médio

11. Escreva um `SELECT` que retorne os alunos nascidos depois de 2007-01-01.
12. Escreva um `SELECT` que retorne os alunos cujo nome comece com a letra "A".
13. Escreva um `SELECT` que retorne os alunos cujo e-mail seja nulo.
14. Qual a diferença entre `WHERE` e `HAVING`?
15. Escreva uma consulta que conte quantos alunos existem no total.
16. Escreva uma consulta que agrupe os alunos por turma e mostre a quantidade de alunos em cada turma.
17. Escreva um `UPDATE` que corrija o e-mail do aluno com `id_aluno = 2` para `"joaosouza@email.com"`.
18. Por que é perigoso executar um `UPDATE` ou `DELETE` sem `WHERE`?
19. Escreva um `SELECT` que retorne as disciplinas do curso com `id_curso = 1`.
20. Explique a diferença entre `DELETE`, `DROP` e `TRUNCATE`.

## Nível 3 — Difícil

21. Escreva uma consulta com `INNER JOIN` que mostre o nome do aluno junto com o nome da disciplina em que está matriculado.
22. Escreva uma consulta com `LEFT JOIN` que mostre todos os alunos, mesmo os que não têm matrícula.
23. Escreva uma consulta que mostre a média de notas de cada aluno, usando `GROUP BY`.
24. Escreva uma consulta que mostre apenas os alunos com média de notas maior que 7, usando `HAVING`.
25. Escreva uma subconsulta que retorne os alunos matriculados na disciplina "Banco de Dados 1".
26. Explique, com um exemplo, por que um relacionamento N:N precisa de uma tabela intermediária.
27. Dada a tabela abaixo, identifique qual forma normal ela viola e explique como corrigi-la:

    | id_aluno | nome | telefones |
    |---|---|---|
    | 1 | Maria | 11999990000, 11988880000 |

28. Explique a diferença entre cardinalidade mínima e cardinalidade máxima, usando um exemplo próprio.
29. Escreva o `CREATE TABLE` de uma tabela associativa para um relacionamento N:N entre `Aluno` e `Disciplina` (sem passar pela `Turma`).
30. Explique por que o comando abaixo é perigoso e reescreva-o de forma segura, supondo que a intenção era remover apenas o aluno com `id_aluno = 5`:

    ```sql
    DELETE FROM aluno;
    ```

---

# 32. Gabarito dos Exercícios

## Nível 1

1. Um SGBD é o software responsável por gerenciar bancos de dados (criar, consultar, alterar, proteger). Exemplos: MySQL, PostgreSQL.
2. O banco de dados é o conjunto de dados organizado; o SGBD é o programa que gerencia esse banco.
3. `SELECT * FROM aluno;`
4. `SELECT nome, email FROM aluno;`
5. `DISTINCT` remove valores duplicados do resultado da consulta.
6. `INSERT INTO curso (nome_curso, carga_horaria) VALUES ('Informática para Internet', 1000);`
7. Chave primária é o atributo que identifica de forma única cada registro de uma tabela, não podendo ser nula nem duplicada.
8. Chave estrangeira é um atributo que referencia a chave primária de outra tabela, criando um relacionamento entre elas.
9. `SELECT * FROM aluno ORDER BY nome ASC;`
10. `SELECT * FROM aluno LIMIT 3;`

## Nível 2

11. `SELECT * FROM aluno WHERE data_nascimento > '2007-01-01';`
12. `SELECT * FROM aluno WHERE nome LIKE 'A%';`
13. `SELECT * FROM aluno WHERE email IS NULL;`
14. `WHERE` filtra linhas antes de agrupar e não aceita funções de agregação; `HAVING` filtra grupos depois do `GROUP BY` e aceita funções de agregação.
15. `SELECT COUNT(*) FROM aluno;`
16. `SELECT id_turma, COUNT(*) AS total_alunos FROM matricula GROUP BY id_turma;`
17. `UPDATE aluno SET email = 'joaosouza@email.com' WHERE id_aluno = 2;`
18. Porque, sem `WHERE`, o comando afeta **todos** os registros da tabela, podendo causar perda ou corrupção massiva de dados.
19. `SELECT * FROM disciplina WHERE id_curso = 1;`
20. `DELETE` remove registros específicos (pode usar `WHERE`) mantendo a tabela; `TRUNCATE` remove todos os registros de uma vez, sem `WHERE`; `DROP` remove a tabela inteira, incluindo sua estrutura.

## Nível 3

21.
```sql
SELECT aluno.nome, disciplina.nome_disciplina
FROM aluno
INNER JOIN matricula ON aluno.id_aluno = matricula.id_aluno
INNER JOIN turma ON matricula.id_turma = turma.id_turma
INNER JOIN disciplina ON turma.id_disciplina = disciplina.id_disciplina;
```

22.
```sql
SELECT aluno.nome, disciplina.nome_disciplina
FROM aluno
LEFT JOIN matricula ON aluno.id_aluno = matricula.id_aluno
LEFT JOIN turma ON matricula.id_turma = turma.id_turma
LEFT JOIN disciplina ON turma.id_disciplina = disciplina.id_disciplina;
```

23.
```sql
SELECT matricula.id_aluno, AVG(nota.valor_nota) AS media
FROM matricula
INNER JOIN nota ON nota.id_matricula = matricula.id_matricula
GROUP BY matricula.id_aluno;
```

24.
```sql
SELECT matricula.id_aluno, AVG(nota.valor_nota) AS media
FROM matricula
INNER JOIN nota ON nota.id_matricula = matricula.id_matricula
GROUP BY matricula.id_aluno
HAVING AVG(nota.valor_nota) > 7;
```

25.
```sql
SELECT nome FROM aluno
WHERE id_aluno IN (
    SELECT matricula.id_aluno
    FROM matricula
    INNER JOIN turma ON matricula.id_turma = turma.id_turma
    INNER JOIN disciplina ON turma.id_disciplina = disciplina.id_disciplina
    WHERE disciplina.nome_disciplina = 'Banco de Dados 1'
);
```

26. Porque uma coluna de uma tabela relacional não pode guardar vários valores ao mesmo tempo sem ferir a normalização (1FN). Assim, para representar que um aluno pode estar em vários cursos e um curso pode ter vários alunos, é preciso uma tabela extra que guarde cada combinação aluno+curso, em vez de tentar colocar uma lista de cursos dentro da linha do aluno.
27. A tabela viola a **1FN**, pois a coluna `telefones` guarda mais de um valor na mesma célula. Correção: criar uma tabela `telefone_aluno(id_telefone, id_aluno, numero)`, com uma linha para cada telefone.
28. A cardinalidade mínima indica se a participação é obrigatória (1) ou opcional (0); a máxima indica o limite (1 ou N). Exemplo: um aluno pode ter de 0 a N matrículas — cardinalidade mínima 0 (opcional) e máxima N (várias).
29.
```sql
CREATE TABLE aluno_disciplina (
    id_aluno INT,
    id_disciplina INT,
    PRIMARY KEY (id_aluno, id_disciplina),
    FOREIGN KEY (id_aluno) REFERENCES aluno(id_aluno),
    FOREIGN KEY (id_disciplina) REFERENCES disciplina(id_disciplina)
);
```
30. É perigoso porque, sem `WHERE`, remove **todos** os alunos da tabela. Forma segura: `DELETE FROM aluno WHERE id_aluno = 5;`

---

# 33. Questões Estilo Prova da ETEC

## Questão 1 (Múltipla escolha)
O que é um SGBD?
a) Um tipo de tabela do banco de dados
b) Um software que gerencia bancos de dados
c) Um comando SQL
d) Um tipo de relacionamento

## Questão 2 (Verdadeiro ou Falso)
( ) A chave estrangeira sempre precisa ser igual à chave primária da tabela onde está.

## Questão 3 (Múltipla escolha)
Em um relacionamento N:N, a forma correta de implementação em SQL é:
a) Colocar a FK das duas tabelas na mesma coluna
b) Criar uma tabela intermediária com as duas FKs
c) Usar apenas `JOIN` sem nenhuma tabela extra
d) Não é possível implementar N:N em SQL

## Questão 4 (SQL)
Escreva um comando `SELECT` que retorne os nomes dos alunos matriculados no curso de id 1, ordenados alfabeticamente.

## Questão 5 (Verdadeiro ou Falso)
( ) `HAVING` pode ser usado no lugar de `WHERE` em qualquer situação, sem diferença de comportamento.

## Questão 6 (Interpretação de tabela)
Observe a tabela abaixo e aponte qual forma normal ela está violando:

| id_pedido | cliente | produtos |
|---|---|---|
| 1 | Ana | Caneta, Caderno, Borracha |

## Questão 7 (Múltipla escolha)
Qual comando remove **apenas os dados** de uma tabela, mantendo sua estrutura, e permite o uso de `WHERE`?
a) `DROP TABLE`
b) `TRUNCATE TABLE`
c) `DELETE FROM`
d) `ALTER TABLE`

## Questão 8 (Interpretação de DER)
Dado o trecho de DER: `[PROFESSOR] (1,1) --- leciona --- (0,N) [TURMA]`, explique com suas palavras o que essa cardinalidade significa para cada lado do relacionamento.

## Questão 9 (Verdadeiro ou Falso)
( ) `INNER JOIN` retorna apenas as linhas que têm correspondência nas duas tabelas envolvidas.

## Questão 10 (SQL)
Escreva um comando que atualize o campo `carga_horaria` do curso com `id_curso = 2` para `900`, de forma segura.

## Questão 11 (Múltipla escolha)
Qual das opções abaixo representa corretamente a 3ª Forma Normal (3FN)?
a) Não pode haver colunas repetidas
b) Não pode haver valores multivalorados em uma célula
c) Não pode haver dependência transitiva entre atributos não-chave
d) Toda tabela precisa ter pelo menos duas chaves estrangeiras

## Questão 12 (Modelagem)
Cite as três entidades principais de um sistema de biblioteca e proponha, ao menos, um relacionamento entre elas com sua cardinalidade.

## Questão 13 (Verdadeiro ou Falso)
( ) Um atributo derivado deve sempre ser armazenado diretamente na tabela, para evitar cálculos futuros.

## Questão 14 (SQL)
Escreva uma consulta que mostre a quantidade de alunos matriculados em cada curso, mas apenas para os cursos que têm mais de 20 alunos.

## Questão 15 (Múltipla escolha)
Em qual situação normalmente se usa uma subconsulta?
a) Para criar uma nova tabela
b) Para usar o resultado de um `SELECT` dentro de outro comando
c) Para deletar registros duplicados automaticamente
d) Para criar uma chave primária composta

## Questão 16 (Interpretação de tabela)
A tabela abaixo poderia ter sua chave primária definida por qual coluna (ou conjunto de colunas)?

| id_aluno | id_curso | data_matricula |
|---|---|---|
| 1 | 10 | 2024-01-10 |
| 1 | 11 | 2024-01-10 |
| 2 | 10 | 2024-01-11 |

## Questão 17 (Verdadeiro ou Falso)
( ) `LIMIT` funciona de forma idêntica em todos os SGBDs, sem nenhuma diferença de sintaxe.

## Questão 18 (SQL)
Escreva o `CREATE TABLE` de uma tabela `livro`, com `id_livro` (chave primária), `titulo` (obrigatório) e `ano_publicacao`.

## Questão 19 (Múltipla escolha)
Qual é a principal diferença entre `LEFT JOIN` e `INNER JOIN`?
a) `LEFT JOIN` é mais rápido em todos os casos
b) `LEFT JOIN` retorna todas as linhas da tabela da esquerda, mesmo sem correspondência; `INNER JOIN` só retorna quando há correspondência nas duas tabelas
c) Não existe diferença, são sinônimos
d) `LEFT JOIN` só pode ser usado com uma tabela

## Questão 20 (Modelagem/Normalização)
Explique, com suas palavras, por que normalizar um banco de dados é importante, citando pelo menos duas anomalias que a normalização evita.

---

# 34. Gabarito das Questões Estilo Prova

**Questão 1:** b) Um software que gerencia bancos de dados. *(O SGBD é o programa que administra o banco, como MySQL ou PostgreSQL.)*

**Questão 2:** Falso. *(A FK precisa apenas referenciar um valor existente na PK da outra tabela — os nomes das colunas podem, inclusive, ser diferentes.)*

**Questão 3:** b) Criar uma tabela intermediária com as duas FKs. *(É a única forma correta de representar N:N em um modelo relacional.)*

**Questão 4:**
```sql
SELECT nome FROM aluno WHERE id_curso = 1 ORDER BY nome ASC;
```

**Questão 5:** Falso. *(`HAVING` filtra grupos após o `GROUP BY` e aceita funções de agregação; `WHERE` filtra linhas antes de agrupar e não aceita agregações — não são intercambiáveis em todas as situações.)*

**Questão 6:** Viola a **1FN**, pois a coluna `produtos` guarda vários valores em uma única célula (não é atômica).

**Questão 7:** c) `DELETE FROM`. *(É o único, entre os citados, que aceita `WHERE` e mantém a estrutura da tabela.)*

**Questão 8:** Cada `Turma` está associada a exatamente um `Professor` (cardinalidade 1,1 do lado Professor), mas um `Professor` pode lecionar de zero a várias turmas (cardinalidade 0,N do lado Turma).

**Questão 9:** Verdadeiro.

**Questão 10:**
```sql
UPDATE curso SET carga_horaria = 900 WHERE id_curso = 2;
```

**Questão 11:** c) Não pode haver dependência transitiva entre atributos não-chave.

**Questão 12:** Exemplo de resposta: entidades `Livro`, `Aluno`, `Emprestimo`. Relacionamento: `Aluno` (0,N) — realiza — (0,N) `Livro`, resolvido pela tabela intermediária `Emprestimo`.

**Questão 13:** Falso. *(Um atributo derivado normalmente **não** precisa ser armazenado, pois pode ser calculado a partir de outro atributo já existente, como a idade a partir da data de nascimento.)*

**Questão 14:**
```sql
SELECT id_curso, COUNT(*) AS total_alunos
FROM aluno
GROUP BY id_curso
HAVING COUNT(*) > 20;
```

**Questão 15:** b) Para usar o resultado de um `SELECT` dentro de outro comando.

**Questão 16:** A chave primária deve ser a combinação (**chave composta**) de `id_aluno` + `id_curso`, pois nenhuma das colunas isoladamente é única (o aluno 1, por exemplo, aparece duas vezes).

**Questão 17:** Falso. *(A sintaxe varia entre SGBDs — por exemplo, o SQL Server usa `TOP` em vez de `LIMIT`.)*

**Questão 18:**
```sql
CREATE TABLE livro (
    id_livro INT PRIMARY KEY AUTO_INCREMENT,
    titulo VARCHAR(150) NOT NULL,
    ano_publicacao INT
);
```

**Questão 19:** b) `LEFT JOIN` retorna todas as linhas da tabela da esquerda, mesmo sem correspondência; `INNER JOIN` só retorna quando há correspondência nas duas tabelas.

**Questão 20:** Resposta esperada (exemplo): a normalização evita, entre outras, a **anomalia de atualização** (precisar alterar o mesmo dado em várias linhas quando ele muda) e a **anomalia de exclusão** (perder informações importantes ao excluir um registro que também guardava, sem necessidade, dados de outra entidade). Ela também reduz a redundância e a inconsistência dos dados.

---

# 35. Erros que Iniciantes Cometem

| Erro comum | Por que acontece | Como evitar |
|---|---|---|
| **Confundir tabela com banco de dados** | Falta de clareza entre os conceitos no início dos estudos | Lembrar que o banco de dados é o "container" que guarda várias tabelas |
| **Confundir PK e FK** | Ambas envolvem chaves e relacionam-se a identificação de registros | Lembrar: PK identifica o próprio registro; FK aponta para o registro de **outra** tabela |
| **Esquecer o WHERE em UPDATE/DELETE** | Pressa ou falta de atenção ao escrever o comando | Sempre rodar um `SELECT` com a mesma condição antes de rodar o `UPDATE`/`DELETE` |
| **Usar WHERE no lugar de HAVING (ou vice-versa)** | Não entender que o `WHERE` age antes do agrupamento e o `HAVING` depois | Lembrar: `WHERE` filtra linhas; `HAVING` filtra grupos (e aceita agregações) |
| **Confundir INNER JOIN e LEFT JOIN** | Não visualizar quais linhas cada JOIN realmente retorna | Montar mentalmente (ou no papel) as tabelas de exemplo e simular o resultado |
| **Criar tabelas com dados repetidos** | Falta de planejamento/normalização antes de criar as tabelas | Sempre passar pelo processo de modelagem (conceitual → lógico → físico) antes do `CREATE TABLE` |
| **Não normalizar o banco** | Pressa para "só fazer funcionar" | Aplicar ao menos as três primeiras formas normais (1FN, 2FN, 3FN) |
| **Escolher tipos de dados inadequados** | Desconhecimento dos tipos disponíveis (ex.: usar `FLOAT` para dinheiro) | Estudar a tabela de tipos de dados e usar `DECIMAL` para valores monetários |
| **Não definir chave primária** | Achar que "não é obrigatório" | Toda tabela deve ter uma PK, para garantir a integridade de entidade |
| **Criar relacionamentos incorretos** | Não identificar corretamente se é 1:1, 1:N ou N:N | Sempre fazer as perguntas de cardinalidade nos dois sentidos do relacionamento antes de implementar |

## Resumo

A maioria dos erros de iniciante em BD1 vem da pressa em "só fazer funcionar" sem passar pelas etapas de modelagem e sem entender profundamente o papel de cada comando/conceito. Revisar a modelagem antes do SQL evita a maior parte desses problemas.

---

# 36. 🧠 Resumão de BD1

| Conceito | O que lembrar |
|---|---|
| **PK** | Identifica unicamente cada registro; não pode ser nula nem repetida |
| **FK** | Aponta para a PK de outra tabela, criando um relacionamento |
| **1:1** | Cada registro se relaciona com no máximo um do outro lado; FK com `UNIQUE` |
| **1:N** | Um registro se relaciona com vários; FK fica no lado "muitos" |
| **N:N** | Vários para vários; sempre exige tabela intermediária |
| **1FN** | Valores atômicos, sem grupos repetidos |
| **2FN** | Atributos dependem da chave composta inteira |
| **3FN** | Sem dependência transitiva entre atributos não-chave |
| **SELECT** | Consulta dados; `*` = todas as colunas |
| **WHERE** | Filtra linhas, antes do agrupamento; não aceita agregação |
| **GROUP BY** | Agrupa linhas para aplicar agregações por grupo |
| **HAVING** | Filtra grupos, depois do `GROUP BY`; aceita agregação |
| **JOIN** | Combina tabelas relacionadas; `INNER` só correspondências, `LEFT`/`RIGHT` trazem tudo de um dos lados |
| **UPDATE/DELETE sem WHERE** | Afeta **todos** os registros — sempre conferir antes com `SELECT` |
| **Índice** | Acelera buscas, mas deixa escritas um pouco mais lentas |
| **Transação** | Conjunto de operações tratado como "tudo ou nada"; `COMMIT` confirma, `ROLLBACK` desfaz |

---

# 37. ⚡ SQL Essencial (Consulta Rápida)

```sql
-- CRIAR BANCO E TABELA
CREATE DATABASE nome_banco;
USE nome_banco;
CREATE TABLE tabela (
    id INT PRIMARY KEY AUTO_INCREMENT,
    coluna VARCHAR(100) NOT NULL
);

-- INSERIR
INSERT INTO tabela (coluna) VALUES ('valor');

-- CONSULTAR
SELECT * FROM tabela;
SELECT coluna FROM tabela WHERE id = 1;
SELECT DISTINCT coluna FROM tabela;

-- FILTROS
SELECT * FROM tabela WHERE coluna = 'valor';
SELECT * FROM tabela WHERE coluna LIKE 'valor%';
SELECT * FROM tabela WHERE coluna BETWEEN 1 AND 10;
SELECT * FROM tabela WHERE coluna IN (1, 2, 3);
SELECT * FROM tabela WHERE coluna IS NULL;

-- ORDENAR E LIMITAR
SELECT * FROM tabela ORDER BY coluna DESC;
SELECT * FROM tabela LIMIT 10;

-- ATUALIZAR (sempre com WHERE!)
UPDATE tabela SET coluna = 'novo_valor' WHERE id = 1;

-- REMOVER (sempre com WHERE!)
DELETE FROM tabela WHERE id = 1;

-- ALTERAR ESTRUTURA
ALTER TABLE tabela ADD COLUMN nova_coluna INT;
ALTER TABLE tabela DROP COLUMN nova_coluna;

-- AGREGAÇÃO E AGRUPAMENTO
SELECT COUNT(*), AVG(coluna), SUM(coluna), MIN(coluna), MAX(coluna) FROM tabela;
SELECT categoria, COUNT(*) FROM tabela GROUP BY categoria;
SELECT categoria, COUNT(*) FROM tabela GROUP BY categoria HAVING COUNT(*) > 5;

-- JOIN
SELECT a.coluna, b.coluna
FROM tabela_a a
INNER JOIN tabela_b b ON a.id = b.id_a;

SELECT a.coluna, b.coluna
FROM tabela_a a
LEFT JOIN tabela_b b ON a.id = b.id_a;

-- SUBCONSULTA
SELECT * FROM tabela WHERE id IN (SELECT id_a FROM outra_tabela WHERE condicao);

-- TRANSAÇÃO
START TRANSACTION;
-- comandos...
COMMIT;
-- ou, em caso de erro: ROLLBACK;
```

---

# 38. Glossário

| Termo | Definição |
|---|---|
| **ACID** | Conjunto de propriedades (Atomicidade, Consistência, Isolamento, Durabilidade) que garantem transações confiáveis |
| **Atributo** | Característica de uma entidade; vira coluna na tabela |
| **Cardinalidade** | Quantidade mínima e máxima de vezes que uma entidade se relaciona com outra |
| **Chave composta** | Chave primária formada por mais de uma coluna |
| **Chave estrangeira (FK)** | Coluna que referencia a chave primária de outra tabela |
| **Chave primária (PK)** | Coluna (ou conjunto de colunas) que identifica unicamente cada registro |
| **CHECK** | Constraint que valida uma condição para os valores de uma coluna |
| **Constraint** | Regra aplicada a uma coluna/tabela para garantir integridade |
| **DDL** | Linguagem de Definição de Dados (`CREATE`, `ALTER`, `DROP`) |
| **DML** | Linguagem de Manipulação de Dados (`INSERT`, `UPDATE`, `DELETE`) |
| **DQL** | Linguagem de Consulta de Dados (`SELECT`) |
| **DCL** | Linguagem de Controle de Dados (`GRANT`, `REVOKE`) |
| **DER** | Diagrama Entidade-Relacionamento; representação gráfica do MER |
| **Domínio** | Conjunto de valores válidos que um atributo pode assumir |
| **Entidade** | "Coisa" do mundo real sobre a qual se guardam dados; vira tabela |
| **GROUP BY** | Agrupa registros para aplicar funções de agregação por grupo |
| **HAVING** | Filtra grupos formados pelo `GROUP BY`, aceitando funções de agregação |
| **Índice** | Estrutura que acelera buscas em uma tabela |
| **Integridade referencial** | Garantia de que uma FK sempre aponte para um valor existente |
| **JOIN** | Comando que combina dados de duas ou mais tabelas relacionadas |
| **MER** | Modelo Entidade-Relacionamento; representação conceitual das entidades e relacionamentos |
| **Normalização** | Processo de organizar tabelas para reduzir redundância e anomalias |
| **Registro/Tupla** | Uma linha de uma tabela |
| **Relacionamento** | Associação entre duas ou mais entidades |
| **SGBD** | Sistema Gerenciador de Banco de Dados; software que administra o banco |
| **SQL** | Structured Query Language; linguagem usada para interagir com bancos relacionais |
| **Subconsulta** | Um `SELECT` dentro de outro comando SQL |
| **TCL** | Linguagem de Controle de Transações (`COMMIT`, `ROLLBACK`) |
| **Transação** | Conjunto de operações tratado como uma única unidade ("tudo ou nada") |
| **WHERE** | Filtra linhas de uma consulta, antes de qualquer agrupamento |

---

*Fim da apostila. Bons estudos! 📚*
