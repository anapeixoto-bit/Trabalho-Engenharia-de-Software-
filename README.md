# Sistema para Academia de Ginástica

**Disciplina:** Engenharia de Software — Atividade Formativa
**Conteúdo:** levantamento de requisitos (RF, RN, RNF) e DFDs orientados a eventos, mais a modelagem de dados de apoio.

\---

## 1\. Cenário e escopo

Uma academia de ginástica deseja desenvolver um sistema para controlar o seu funcionamento.

* Os alunos são organizados em **turmas**; cada turma está associada a **um tipo específico de atividade** (ex.: musculação, dança, ginástica).
* Cada turma é orientada por **um único instrutor** e possui **um aluno monitor**, que auxilia o instrutor durante as atividades.
* Um instrutor pode orientar **várias turmas**, inclusive de tipos de atividade diferentes.
* Um aluno pode estar matriculado em **várias turmas** (atividades diferentes) e pode ser monitor de **no máximo uma turma**.
* Para cada matrícula em uma turma, o sistema mantém o **registro das ausências** do aluno.

### 1.1 Dados cadastrados (conforme o enunciado)

|Entidade|Dados|
|-|-|
|**Turma**|número de alunos, horário da aula, duração da aula, data de início, data de término, tipo de atividade|
|**Instrutor**|RG, nome, data de nascimento, titulação, telefones para contato (um ou mais)|
|**Aluno**|código de matrícula, data de matrícula, nome, endereço, telefone, data de nascimento, altura, peso|
|**Ausência**|aluno, turma e data da ausência (por matrícula em turma)|

### 1.2 Atores

|Ator|Papel|
|-|-|
|**Administração da academia**|Realiza os cadastros (atividades, instrutores, turmas) e designa/substitui instrutor e monitor. *(Premissa: o enunciado não diz quem opera o cadastro; adotou-se este ator.)*|
|**Aluno**|Fornece seus dados e solicita matrícula em turmas. O monitor é um aluno.|
|**Instrutor**|Orienta turmas, registra ausências e consulta turmas.|

\---

## 2.2 Requisitos Funcionais (RF)

|Código|Requisito funcional|
|-|-|
|RF01|**Cadastrar atividades:** o sistema deve permitir cadastrar os tipos de atividade oferecidos (ex.: musculação, dança, ginástica).|
|RF02|**Cadastrar instrutores:** o sistema deve permitir cadastrar instrutores com RG, nome, data de nascimento, titulação e um ou mais telefones.|
|RF03|**Cadastrar alunos:** o sistema deve permitir cadastrar alunos com código de matrícula, data de matrícula, nome, endereço, telefone, data de nascimento, altura e peso.|
|RF04|**Cadastrar turmas:** o sistema deve permitir criar turmas informando tipo de atividade, número de alunos, horário e duração da aula, data de início e data de término.|
|RF05|**Definir e substituir o instrutor da turma:** o sistema deve associar um único instrutor a cada turma e permitir sua substituição.|
|RF06|**Definir e substituir o monitor da turma:** o sistema deve associar um único aluno monitor a cada turma e permitir sua substituição.|
|RF07|**Matricular aluno em turmas:** o sistema deve permitir que um aluno seja matriculado em uma ou mais turmas, de atividades diferentes.|
|RF08|**Registrar ausências:** o sistema deve permitir registrar a ausência de um aluno (data) em uma turma na qual está matriculado.|
|RF09|**Consultar ausências:** o sistema deve permitir consultar as ausências por aluno e por turma.|
|RF10|**Consultar turmas:** o sistema deve permitir consultar as turmas com atividade, instrutor, monitor, horário, período e alunos matriculados.|

## 2.3 Regras de Negócio (RN)

|Código|Regra de negócio|
|-|-|
|RN01|Cada turma está associada a **exatamente um** tipo de atividade.|
|RN02|Cada turma é orientada por **um único** instrutor.|
|RN03|Um instrutor pode orientar **várias turmas**, inclusive de tipos de atividade diferentes.|
|RN04|Cada turma possui **exatamente um** aluno monitor, que auxilia o instrutor durante as atividades.|
|RN05|Um aluno pode ser monitor de **no máximo uma** turma.|
|RN06|Um aluno pode estar matriculado em **várias turmas**, de atividades diferentes.|
|RN07|Para cada matrícula em uma turma deve ser mantido o **registro das ausências** do aluno.|
|RN08|Só se registra ausência de aluno **matriculado** na turma; a mesma ausência (aluno, turma, data) não pode ser registrada duas vezes. *(decisão de projeto)*|
|RN09|A data de término da turma não pode ser anterior à data de início. *(decisão de projeto)*|
|RN10|O número de alunos da turma corresponde à quantidade de matrículas na turma (atributo derivado). *(decisão de projeto)*|
|RN11|O código de matrícula identifica unicamente o aluno; o RG identifica unicamente o instrutor. *(decisão de projeto)*|

## 2.4 Requisitos Não Funcionais (RNF)

|Código|Requisito não funcional|
|-|-|
|RNF01|**Autenticação:** o sistema deve exigir login e senha; as senhas devem ser armazenadas de forma criptografada (hash).|
|RNF02|**Proteção de dados:** o sistema deve proteger os dados pessoais dos alunos (incluindo altura e peso) contra acesso não autorizado, conforme a LGPD (Lei nº 13.709/2018).|
|RNF03|**Controle de acesso por perfil:** cada usuário só acessa as funcionalidades autorizadas ao seu perfil (Administração: todos os cadastros; Instrutor: consulta de turmas e registro de ausências).|
|RNF04|**Integridade dos dados:** o sistema deve garantir, no banco de dados, as chaves, restrições de unicidade e regras de integridade referencial (ver `modelo\_fisico.sql`).|
|RNF05|**Usabilidade:** as telas de cadastro e de registro de ausência devem ser simples o bastante para uso sem treinamento prolongado. *(sugestão)*|
|RNF06|**Disponibilidade e backup:** o sistema deve possuir cópia de segurança periódica dos dados. *(sugestão)*|

\---

## 2.5 Diagramas de Fluxo de Dados (DFD) orientados a eventos

[![Modelo Fluxo de Dadosl]](img/Diagramas_de _Fluxo_de _Dados.png)


## 3. Modelagem de dados (apoio)

### Modelo conceitual
[![Modelo conceitual](img/conceitual.png)

### Modelo lógico
[![Modelo lógico](img/logico.png)](img/logico.png)

### Modelo físico
[![Modelo físico](img/fisico.png)](img/fisico.png)
