# Métodos

Para facilitar o desenvolvimento das customizações e integrações o SAM conta com uma vasta biblioteca de métodos e funções para realizar os mais diversos tipos de processos. Em definição, um método é equivalente a uma função, subrotina ou procedimento escrito em uma certa linguagem de programação.

!!! Nota
	A partir de agora veremos alguns termos que são exclusivos do SAM, recomendamos fortemente que você leia e conheça um pouco mais sobre a estrutura do SAM. Visite nosso [manual](http://samdoc.info/manuald?id=57762).
	
Os métodos que veremos a seguir, pode ou não estar disponível para utilização nos [Tipos de Processos](/processos) existentes no SAM. Estes processos são dividos em dois grupos, os que são criados a partir do SAMDEV e os Scripts de Operações que são criados a partir de cada tarefa específica.

Cada processo será identificado como: <small>:red_square: Fórmulas, :blue_square: Listagens, :brown_square: Cubos de Decisões, :green_square: Servlets, :purple_square: Script de Operações.</small>

## `obterEmpresaAtiva`
<span style="font-size: 10px;float: right; margin-top:-40px">:red_square: :blue_square: :brown_square: :green_square: :purple_square:</span>

----

Este método retorna um objeto do tipo Aac10 contendo os dados da empresa ativa.

=== "Exemplo"
	``` groovy
	def aac10 = obterEmpresaAtiva()
	```

## `obterUsuarioLogado`
<span style="font-size: 10px;float: right; margin-top:-40px">:red_square: :blue_square: :brown_square: :green_square: :purple_square:</span>

----

Este método retorna um objeto do tipo Aab10 contendo os dados do usuário logado no sistema.

=== "Exemplo"
	``` groovy
	def aab10 = obterUsuarioLogado()
	```
	
## `getAcessoAoBanco`
<span style="font-size: 10px;float: right; margin-top:-40px">:red_square: :blue_square: :brown_square: :green_square:</span>

----

Este método retorna uma coleção de métodos uteis para manipulação do banco de dados descritos a baixo:

### `buscarListaDeTableMap`
----

Este métodos retorna uma lista de TableMap contendo os registros obtidos a partir da execução de uma SQL.

**Argumentos: **
:	- arg1: String - SQL a ser executada.
:	- arg2: ? boolean - Define se o resultado será paginado.
:	- arg3: ? int - Página a iniciar.
:	- arg4: ? Array[[Parametro](/parametro)] - Parêmetros existentes na SQL.

=== "Exemplo"
	``` groovy
	getAcessoAoBanco().buscarListaDeTableMap("SELECT aac10codigo, aac10rs FROM aac10")
	```
=== "Retorno"
	``` json
	{
		0: {
			"aac10codigo": "00001",
			"aac10rs": "Empresa Fictícia LTDA"
		},
		1: {
			"aac10codigo": "00002",
			"aac10rs": "Empresa Teste LTDA"
		}
	}
	```
	
### `buscarUnicoTableMap`
----

Este métodos retorna um único TableMap contendo o registro obtido a partir da execução de uma SQL.

**Argumentos: **
:	- arg1: String - SQL a ser executada.
:	- arg2: ? Array[[Parametro](/parametro)] - Parêmetros existentes na SQL.

=== "Exemplo"
	``` groovy
	getAcessoAoBanco().buscarUnicoTableMap("SELECT aac10codigo, aac10rs FROM aac10 WHERE aac10codigo = '00001'")
	```
=== "Retorno"
	``` json
	{
		"aac10codigo": "00001",
		"aac10rs": "Empresa Fictícia LTDA"
	}
	```
	
### `buscarListaDeRegistros`
----

Este métodos retorna uma lista de Registros obtidos a partir da execução de uma SQL.

**Argumentos: **
:	- arg1: String - SQL a ser executada.
:	- arg2: ? boolean - Define se o resultado será paginado.
:	- arg3: ? int - Página a iniciar.
:	- arg4: ? Array[[Parametro](/parametro)] - Parêmetros existentes na SQL.

=== "Exemplo"
	``` groovy
	getAcessoAoBanco().buscarListaDeRegistros("SELECT aac10id, aac10codigo, aac10rs FROM aac10")
	```
=== "Retorno"
	``` java
	{
		0: object(Aac10)#1 (3) {
			private aac10id = 12345,
			private aac10codigo = "00001",
			private aac10rs = "Empresa Fictícia LTDA"
		},
		1: object(Aac10)#2 (3) {
			private aac10id = 12346,
			private aac10codigo = "00002",
			private aac10rs = "Empresa Teste LTDA"
		}
	}
	```
	
### `buscarRegistroUnico`
----

Este métodos retorna um único Registro obtido a partir da execução de uma SQL.

**Argumentos: **
:	- arg1: String - SQL a ser executada.
:	- arg2: ? Array[[Parametro](/parametro)] - Parêmetros existentes na SQL.

=== "Exemplo"
	``` groovy
	getAcessoAoBanco().buscarRegistroUnico("SELECT aac10id, aac10codigo, aac10rs FROM aac10 WHERE aac10id = 12345")
	```
=== "Retorno"
	``` java
	object(Aac10)#1 (3) {
		private aac10id = 12345,
		private aac10codigo = "00001",
		private aac10rs = "Empresa Fictícia LTDA"
	}
	```

### `buscarMultiResultSet`
----

Este métodos retorna um objeto do tipo MultiResultSet contendo os registros obtidos a partir da execução de uma SQL.

**Argumentos: **
:	- arg1: String - SQL a ser executada.
:	- arg2: ? Array[[Parametro](/parametro)] - Parêmetros existentes na SQL.

=== "Exemplo"
	``` groovy
	getAcessoAoBanco().buscarMultiResultSet("SELECT aac10codigo, aac10rs FROM aac10")
	```
=== "Retorno"
	``` java
	object(MultiResultSet)#1 (2) {
		aac10codigo = "00001",
		aac10rs = "Empresa Fictícia LTDA"
	}
	```
	
### `obterMapDeRegistros`
----

Este métodos retorna um Mapa contendo os registros obtidos a partir da execução de uma SQL.

**Argumentos: **
:	- arg1: String - SQL a ser executada.
:	- arg2: String - Nome da coluna que será a chave.
:	- arg3: String - Nome da coluna que será o valor.

=== "Exemplo"
	``` groovy
	getAcessoAoBanco().buscarMultiResultSet("SELECT aac10codigo, aac10rs FROM aac10", "aac10codigo", "aac10rs")
	```
=== "Retorno"
	``` java
	object(HashMap)#1 (2) {
		"aac10codigo": "00001",
		"aac10rs": "Empresa Fictícia LTDA"
	}
	```
	
### `obterListaDeBigDecimal`
----

Este métodos retorna uma lista de Decimais obtidos a partir da execução de uma SQL.

**Argumentos: **
:	- arg1: String - SQL a ser executada.
:	- arg2: ? boolean - Define se o resultado será paginado.
:	- arg3: ? int - Página a iniciar.
:	- arg4: ? Array[[Parametro](/parametro)] - Parêmetros existentes na SQL.

=== "Exemplo"
	``` groovy
	getAcessoAoBanco().obterListaDeBigDecimal("SELECT eaa01valor FROM Eaa01")
	```
=== "Retorno"
	``` java
	{
		0: 256.012
		1: 45.6988
	}
	```
	
### `obterBigDecimal`
----

Este métodos retorna um Decimal obtido a partir da execução de uma SQL.

**Argumentos: **
:	- arg1: String - SQL a ser executada.
:	- arg2: ? Array[[Parametro](/parametro)] - Parêmetros existentes na SQL.

=== "Exemplo"
	``` groovy
	getAcessoAoBanco().obterBigDecimal("SELECT eaa01valor FROM eaa01 WHERE eaa01id = 12345")
	```
=== "Retorno"
	``` java
	457.65559
	```

### `obterListaDeInteger`
----

Este métodos retorna uma lista de Inteiros obtidos a partir da execução de uma SQL.

**Argumentos: **
:	- arg1: String - SQL a ser executada.
:	- arg2: ? boolean - Define se o resultado será paginado.
:	- arg3: ? int - Página a iniciar.
:	- arg4: ? Array[[Parametro](/parametro)] - Parêmetros existentes na SQL.

=== "Exemplo"
	``` groovy
	getAcessoAoBanco().obterListaDeInteger("SELECT eaa01esMov FROM Eaa01")
	```
=== "Retorno"
	``` java
	{
		0: 0
		1: 1
	}
	```
	
### `obterInteger`
----

Este métodos retorna um Inteiro obtido a partir da execução de uma SQL.

**Argumentos: **
:	- arg1: String - SQL a ser executada.
:	- arg2: ? Array[[Parametro](/parametro)] - Parêmetros existentes na SQL.

=== "Exemplo"
	``` groovy
	getAcessoAoBanco().obterInteger("SELECT eaa01esMov FROM eaa01 WHERE eaa01id = 12345")
	```
=== "Retorno"
	``` java
	1
	```

### `obterListaDeDate`
----

Este métodos retorna uma lista de objetos do tipo LocalDate obtidos a partir da execução de uma SQL.

**Argumentos: **
:	- arg1: String - SQL a ser executada.
:	- arg2: ? boolean - Define se o resultado será paginado.
:	- arg3: ? int - Página a iniciar.
:	- arg4: ? Array[[Parametro](/parametro)] - Parêmetros existentes na SQL.

=== "Exemplo"
	``` groovy
	getAcessoAoBanco().obterListaDeDate("SELECT abb01data FROM abb01")
	```
=== "Retorno"
	``` java
	{
		0: "2021-01-01"
		1: "2020-02-10"
	}
	```
	
### `obterDate`
----

Este métodos retorna um objeto do tipo LocalDate obtido a partir da execução de uma SQL.

**Argumentos: **
:	- arg1: String - SQL a ser executada.
:	- arg2: ? Array[[Parametro](/parametro)] - Parêmetros existentes na SQL.

=== "Exemplo"
	``` groovy
	getAcessoAoBanco().obterDate("SELECT abb01data FROM abb01data WHERE abb01id = 12345")
	```
=== "Retorno"
	``` java
	"2021-12-31"
	```
	
### `obterListaDeString`
----

Este métodos retorna uma lista de String obtidas a partir da execução de uma SQL.

**Argumentos: **
:	- arg1: String - SQL a ser executada.
:	- arg2: ? boolean - Define se o resultado será paginado.
:	- arg3: ? int - Página a iniciar.
:	- arg4: ? Array[[Parametro](/parametro)] - Parêmetros existentes na SQL.

=== "Exemplo"
	``` groovy
	getAcessoAoBanco().obterListaDeString("SELECT abh80nome FROM abh80")
	```
=== "Retorno"
	``` java
	{
		0: "José Pereira Lima"
		1: "Alberto Mendes"
	}
	```
	
### `obterString`
----

Este métodos retorna uma String obtida a partir da execução de uma SQL.

**Argumentos: **
:	- arg1: String - SQL a ser executada.
:	- arg2: ? Array[[Parametro](/parametro)] - Parêmetros existentes na SQL.

=== "Exemplo"
	``` groovy
	getAcessoAoBanco().obterString("SELECT abh80nome FROM abh80 WHERE abh80id = 12345")
	```
=== "Retorno"
	``` java
	"Pedro Siqueira de Campos"
	```

### `obterListaDeLong`
----

Este métodos retorna uma lista de Log obtidos a partir da execução de uma SQL.

**Argumentos: **
:	- arg1: String - SQL a ser executada.
:	- arg2: ? boolean - Define se o resultado será paginado.
:	- arg3: ? int - Página a iniciar.
:	- arg4: ? Array[[Parametro](/parametro)] - Parêmetros existentes na SQL.

=== "Exemplo"
	``` groovy
	getAcessoAoBanco().obterListaDeLong("SELECT aac10id FROM aac10")
	```
=== "Retorno"
	``` java
	{
		0: 9513697880
		1: 1055006470
	}
	```
	
### `obterLong`
----

Este métodos retorna um Long obtido a partir da execução de uma SQL.

**Argumentos: **
:	- arg1: String - SQL a ser executada.
:	- arg2: ? Array[[Parametro](/parametro)] - Parêmetros existentes na SQL.

=== "Exemplo"
	``` groovy
	getAcessoAoBanco().obterLong("SELECT aac10id FROM aac10 WHERE aac10id = 1234567890")
	```
=== "Retorno"
	``` java
	1234567890
	```
	
### `buscarRegistroUnicoById`
----

Este método retorna um registro de uma tabela pelo id informado como argumento.

**Argumentos: **
:	- arg1: String - Nome da tabela.
:	- arg2: Long - ID do registro.

=== "Exemplo"
	``` groovy
	getAcessoAoBanco().buscarRegistroUnicoById("Aah03", 12345)
	```
=== "Retorno"
	``` java
	object(Aah03)#1 (2) {
		private aah03id = 12345,
		private aah03tabela = "Tabela Custom"
	}
	```
	
### `buscarRegistroUnicoByCriterion`
----

Este método retorna um registro de uma tabela filtrado por um [Criterion](/criterions).

**Argumentos: **
:	- arg1: String - Nome da tabela.
:	- arg2: Criterion - Filtro.

=== "Exemplo"
	``` groovy
	return getAcessoAoBanco().buscarRegistroUnicoByCriterion("Aah03", Criterions.eq("aah03id", 12345))
	```
=== "Retorno"
	``` java
	object(Aah03)#1 (2) {
		private aah03id = 12345,
		private aah03tabela = "Tabela Custom"
	}
	```
	
## `criarParametroSql`
<span style="font-size: 10px;float: right; margin-top:-40px">:red_square: :blue_square: :brown_square: :green_square:</span>

----

Este método retorna um objeto do tipo [Parametro](/parametro) para ser utilizado nos métodos que realizam a manipulação do banco de dados que vimos acima.

**Argumentos: **
:	- arg1: String - Chave
:	- arg2: Object - Valor

=== "Exemplo"
	``` groovy
	def sql = " SELECT * FROM Abm01 WHERE abm01codigo = :codigo AND abm01tipo = :tipo "
	
	def paramCodigo = criarParametroSql("codigo", "0101001")
	def paramTipo = criarParametroSql("tipo", 0)
	
	return getAcessoAoBanco().buscarRegistroUnico(sql, paramCodigo, paramTipo)
	```
	
## `obterWherePadrao`
<span style="font-size: 10px;float: right; margin-top:-40px">:red_square: :blue_square: :brown_square: :green_square: :purple_square:</span>

----

Este método retorna um WHERE filtrando pelos [Campos Default](http://samdoc.info/manuald?id=57791) para ser utilizado em SQLs.

**Argumentos: **
:	- arg1: String - Nome da Classe
:	- arg2: ? String - Comparador Ex.: WHERE, AND, OR

=== "Exemplo"
	``` groovy
	def sql = "SELECT * FROM Eaa01 WHERE eaa01id = 123 " + obterWherePadrao("Eaa01", "AND")
	```
=== "Retorno"
	``` java
	"SELECT * FROM Eaa01 WHERE eaa01id = 123 AND eaa01gc IN (1, 2, 3)"
	```
	
## `selecionarAlinhamento`
<span style="font-size: 10px;float: right; margin-top:-40px">:red_square: :blue_square:</span>

----

O alinhamento de valores permite fazer um alinhamento dos campos de registros contidos em um leiaute, uma fórmula, em listagens para alinhar campos livres do sistema (Json), possibilitando usar nas fórmulas um nome padronizado.
Este método seleciona qual alinhamento de valores será utilizado no script

**Argumentos: **
:	- arg1: String - Código do alinhamento

=== "Exemplo"
	``` groovy
	selecionarAlinhamento("0001")
	```

## `getCampo`
<span style="font-size: 10px;float: right; margin-top:-40px">:red_square: :blue_square:</span>

----

Este método retorna o campo informado no alinhamento de valores pelo conteúdo do registro. Este método deve ser utilizado após a utilização do método `selecionarAlinhamento`

**Argumentos: **
:	- arg1: String - Registro
:	- arg2: String - Campo

=== "Exemplo"
	``` groovy
	getCampo("C100", "ICMS")
	```
	
## `getSession`
<span style="font-size: 10px;float: right; margin-top:-40px">:red_square: :blue_square: :brown_square: :green_square:</span>

----

Este método retorna um objeto do tipo [Session](/session).

=== "Exemplo"
	``` groovy
	def session = getSession()
	session.persist(abc)
	```

## `interromper`
<span style="font-size: 10px;float: right; margin-top:-40px">:red_square: :blue_square: :brown_square: :green_square: :purple_square:</span>

----

Este método lança uma exceção ao processo, interrompendo-o.

**Argumentos: **
:	- arg1: String - Mensagem a ser exibida.

=== "Exemplo"
	``` groovy
	interromper("Você não tem permissão para continuar.")
	```
	
## `converterCorpoRequisicaoParaString`
<span style="font-size: 10px;float: right; margin-top:-40px">:green_square:</span>

----

Este método converte o corpo da requisição enviado a um Servlet para String.

=== "Exemplo"
	``` groovy
	def body = converterCorpoRequisicaoParaString()
	```
	
## `converterCorpoRequisicaoParaObjeto`
<span style="font-size: 10px;float: right; margin-top:-40px">:green_square:</span>

----

Este método converte o corpo da requisição enviado a um Servlet para um objeto do tipo informado como argumento.

**Argumentos: **
:	- arg1: Class<?> - Tipo do objeto que será convertido

=== "Exemplo"
	``` groovy
	TableMap body = converterCorpoRequisicaoParaObjeto(TableMap.class)
	```
	
## `getParametroRequisicao`
<span style="font-size: 10px;float: right; margin-top:-40px">:green_square:</span>

----

Este método retorna o conteudo de um parêmetro enviado ao Servlet via URL.

**Argumentos: **
:	- arg1: String - Nome do parâmetro

=== "Exemplo"
	``` groovy
	// URL: https://endereco.sam/caminhoServlet?id_registro=12345
	
	def id_registro = getParametroRequisicao("id_registro")
	```

## Métodos get()
<span style="font-size: 10px;float: right; margin-top:-40px">:red_square: :blue_square: :brown_square:</span>

----

Sempre que uma Listagem, um Cubo ou uma Fórmula é executado, alguns dados precisam ser enviados para o processo, estes dados podem ser conteudo dos filtros, no caso dos processos de extração de dados ou das tarefas que enviam informações para as fórmulas. O envio deste dado é feito através de um Mapa de chave e valor, para recuperar estes dados utilizamos o método get() e suas variações.

Exemplo: Em um relatório existe um campo de data e foi atribuido o nome `dataDeInicio`.

``` html
<m-date label="Data de Inicio" v-model="filtros.dataDeInicio" />
```

Para recuperar o conteudo deste campo a partir do código groovy utilizamos o método `get()`.

``` groovy
def dataDeInicio = get("dataDeInicio")
```

Este método por si só retorna um objeto. Cantamos com alguma variações deste método que nos trazem os dados já convertidos.

| Método              | Retorno           | Método              | Retorno           |
| ------------------- | ----------------- | ------------------- | ----------------- |
| getString()         | Texto             | getLocalDate()      | Data              |
| getBoolean()        | Booleano          | getLocalTime()      | Hora              |
| getInteger()        | Inteiro           | getIntervaloDatas() | Array de Datas    |
| getLong()           | Longo             | getListLong()       | Lista de Longos   |
| getBigDecimal()     | Decimal           | getListInteger()    | Lista de Inteiros |


## `getCritDataInterval`
<span style="font-size: 10px;float: right; margin-top:-40px">:red_square: :blue_square: :brown_square:</span>

----

Este método cria um [Criterion](/criterion) a partir de duas datas.

**Argumentos: **
:	- arg1: Array[LocalDate] - Intervalo de datas
:	- arg2: String - Nome do campo na base de dados

=== "Exemplo"
	``` groovy
	def datas = ['2021-01-01', '2021-12-31']
	getCritDataInterval(datas, "abb01data")
	```
	
## `getWhereDataInterval`
<span style="font-size: 10px;float: right; margin-top:-40px">:red_square: :blue_square: :brown_square:</span>

----

Este método cria uma String com um Where a partir de duas datas.

**Argumentos: **
:	- arg1: String - Operador (WHERE, AND, OR)
:	- arg2: Array[LocalDate] - Intervalo de datas
:	- arg3: String - Nome do campo na base de dados

=== "Exemplo"
	``` groovy
	def datas = ['2021-01-01', '2021-12-31']
	getWhereDataInterval("WHERE", datas, "abb01data")
	```
	
## `getWhereIntegerInterval`
<span style="font-size: 10px;float: right; margin-top:-40px">:red_square: :blue_square: :brown_square:</span>

----

Este método cria uma String com um Where a partir de dois inteiros.

**Argumentos: **
:	- arg1: String - Operador (WHERE, AND, OR)
:	- arg2: Integer - Número Inicial
:	- arg3: Integer - Número Final
:	- arg4: String - Nome do campo na base de dados

=== "Exemplo"
	``` groovy
	getWhereIntegerInterval("WHERE", 1, 9, "eaa01esMov")
	```

## `addWhereOrAnd`
<span style="font-size: 10px;float: right; margin-top:-40px">:red_square: :blue_square: :brown_square:</span>

----

Este método cria uma String com um Where a partir de um Array de dados.

**Argumentos: **
:	- arg1: String - Operador (AND, OR)
:	- arg2: Array[String] - Condições do Where

=== "Exemplo"
	``` groovy
	def condicoes = ["abm01tipo = 1", "abm01codigo = '0101001'"]
	addWhereOrAnd("AND", condicoes)
	```

## `round`
<span style="font-size: 10px;float: right; margin-top:-40px">:red_square: :blue_square: :brown_square:</span>

----

Este arredenda um valor Decimal para a quantidade de casas definido no argumento.

**Argumentos: **
:	- arg1: BigDecimal - Dicimal a arredondar
:	- arg2: int - Casas decimais

=== "Exemplo"
	``` groovy
	def decimal = 12.8867899
	def duasCasas = round(decimal, 2)
	```
=== "Retorno"
	``` java
	12.89
	```
	
## `trunc`
<span style="font-size: 10px;float: right; margin-top:-40px">:red_square: :blue_square: :brown_square:</span>

----

Este trunca um valor Decimal para a quantidade de casas definido no argumento.

**Argumentos: **
:	- arg1: BigDecimal - Dicimal a arredondar
:	- arg2: int - Casas decimais

=== "Exemplo"
	``` groovy
	def decimal = 12.8867899
	def duasCasas = trunc(decimal, 3)
	```
=== "Retorno"
	``` java
	12.886
	```

<br>

-----

## Métodos do Script de Operações

Um Script de Operação permite a manipulação dos componentes de tela do SAM, interferir em ações ou processos ou até mesmo criar componentes, ações ou processos customizados.

Os componentes de tela do SAM são construidos a partir de componentes [Swing](), sendo assim, os métodos aplicaveis aos componentes swing são aplicados aos componentes do SAM.

As tarefas do SAM são divididas em dois tipos: <small>:red_square: Cadastros e :blue_square: Processos</small>.

## `execute`
<span style="font-size: 10px;float: right; margin-top:-40px">:red_square: :blue_square:</span>

----

Este método é executado antes da tarefa ser aberta, nele serão feitas as alterações em componentes visuais ou processos da tela.

## `preSalvar`
<span style="font-size: 10px;float: right; margin-top:-40px">:red_square:</span>

----

Este método é executado nos cadastros sempre que o usuário salvar (F9) um registro.

## `posSalvar`
<span style="font-size: 10px;float: right; margin-top:-40px">:red_square:</span>

----

Este método é executado nos cadastros após o usuário salvar (F9) um registro.

## Métodos de Interação:

Métodos criados para avisar, alertar, interromper e questionar o usuário.

### `exibirInformacao`
<span style="font-size: 10px;float: right; margin-top:-40px">:red_square: :blue_square:</span>

----

Exibir em uma tela uma mensagem apenas informativa.

**Argumentos: **
:	- arg1: String - Mensagem a ser exibida

=== "Exemplo"
	``` groovy
	exibirInformacao("Olá Mundo!")
	```

### `exibirAtencao`
<span style="font-size: 10px;float: right; margin-top:-40px">:red_square: :blue_square:</span>

----

Exibir em uma tela uma mensagem de alerta/atenção porém sem interromper o processo.

**Argumentos: **
:	- arg1: String - Mensagem a ser exibida

=== "Exemplo"
	``` groovy
	exibirAtencao("O saldo da conta corrente está negativo.")
	```

### `exibirQuestao`
<span style="font-size: 10px;float: right; margin-top:-40px">:red_square: :blue_square:</span>

----

Exibir em uma tela uma questão com dois botões [SIM, NÃO] retornando [false] para [NÃO] e [true] para [SIM].

**Argumentos: **
:	- arg1: String - Mensagem a ser exibida

=== "Exemplo"
	``` groovy
	def resposta = exibirQuestao("Deseja continuar o processo?")
	```

## Métodos para Banco de Dados:

Métodos para fazer consultas, salvar e deletar dados no banco conforme a SQL criada pelo usuário.

### `executarConsulta`
<span style="font-size: 10px;float: right; margin-top:-40px">:red_square: :blue_square:</span>

----

Executa a SQL informada no banco de dados.

**Argumentos: **
:	- arg1: String - SQL a ser executada no banco de dados

=== "Exemplo"
	``` groovy
	executarConsulta("SELECT * FROM Abh80 LIMIT 1")
	```

### `executarSalvarOuExcluir`
<span style="font-size: 10px;float: right; margin-top:-40px">:red_square: :blue_square:</span>

----

Executa uma SQL sem retorno, ou seja, apenas uma SQL para salvar (INSERT/UPDATE) ou excluir (DELETE) um registro no banco de dados.

**Argumentos: **
:	- arg1: String - SQL a ser executada no banco de dados

=== "Exemplo"
	``` groovy
	executarSalvarOuExcluir("UPDATE Abh80 SET abh80nome = 'José')
	```

## Métodos para Manipulação da tela:

Métodos para fazer alterações em componentes da tela.

### `ocultarColunas`
<span style="font-size: 10px;float: right; margin-top:-40px">:red_square: :blue_square:</span>

----

Oculta uma coluna de uma determinada Spread (Tabela) da tela.

**Argumentos: **
:	- arg1: MSpread - Spread que terá as colunas ocultas
:	- arg1: int - Índice das colunas que serão ocultas separadas por virgula

=== "Exemplo"
	``` groovy
	def spread = getComponente("nomeSpread")
    ocultarColunas(spread, 0, 3, 5, 10)
	```

### `criarBotao`
<span style="font-size: 10px;float: right; margin-top:-40px">:red_square: :blue_square:</span>

----

Cria um botão customizado na parte inferior da tela devendo receber dois argumentos: o primeiro indicando qual o texto do botão e o segundo uma função que será executada ao clicar.

**Argumentos: **
:	- arg1: String - Texto que será exibido no botão
:	- arg1: ActionListener - Função que será executada ao clicar

=== "Exemplo"
	``` groovy
	criarBotao("Salvar", { 
		exibirInformacao("Você clicou no botão") 
	})
	```

### `mostrarBotoes`
<span style="font-size: 10px;float: right; margin-top:-40px">:red_square: :blue_square:</span>

----

Este método deve ser chamado logo após a criação dos botões customizados para que eles possam ser exibidos na tela.

**Argumentos: **
:	- arg1: int - Tamanho dos botões, por padrão é 100.

=== "Exemplo"
	``` groovy
	criarBotao("Salvar", { salvarRegistro() })
	mostrarBotoes(150)
	```

### `alterarTamanhoTela`
<span style="font-size: 10px;float: right; margin-top:-40px">:red_square: :blue_square:</span>

----

Altera a altura e a largura da tela somando os valores recebido como argumento ao tamanho original.

**Argumentos: **
:	- arg1: int - Largura que a tela será alterada
:	- arg1: int - Altura que a tela será alterada

=== "Exemplo"
	``` groovy
	alterarTamanhoTela(10, 50)
	```
