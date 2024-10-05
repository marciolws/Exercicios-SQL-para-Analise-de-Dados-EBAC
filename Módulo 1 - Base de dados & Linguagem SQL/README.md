<img src="https://raw.githubusercontent.com/marciolws/Curso_EBAC_Cientista_de_Dados/refs/heads/main/EBAC-media-utils/logo/newebac_logo_black_half.png" alt="ebac-logo">

---

# **Módulo 1** | SQL: Base de dados & Linguagem SQL

Aluno [Marcio da Silva](https://www.linkedin.com/in/marcio-d-silva/)<br>

Data: 05 de outubro de 2024.

---

## Atividades

### **1 Criação da tabela de clientes**

```sql
CREATE EXTERNAL TABLE clientes(
	id BIGINT,
	idade BIGINT,
	sexo STRING,
	dependentes BIGINT,
	escolaridade STRING,
	tipo_cartao STRING,
	limite_credito DOUBLE,
	valor_transacoes_12m DOUBLE,
	qtd_transacoes_12m BIGINT
)
ROW FORMAT SERDE 'org.apache.hadoop.hive.serde2.OpenCSVSerde'
WITH SERDEPROPERTIES (
	'separatorChar' = ',',
	'quoteChar' = '"',
	'escapeChar' = '\\'
)
STORED AS TEXTFILE
LOCATION 's3://ebac-robertohatiro-modulo1/'
```

### **2. Explorando os dados da tabela de clientes**

#### [**2.1. Query 1**](https://github.com/marciolws/Exercicios-SQL-para-Analise-de-Dados-EBAC/blob/main/Módulo%201%20-%20Base%20de%20dados%20%26%20Linguagem%20SQL/query_1.csv)
```sql
SELECT *
FROM clientes;
```

#### [**2.2. Query 2**](https://github.com/marciolws/Exercicios-SQL-para-Analise-de-Dados-EBAC/blob/main/Módulo%201%20-%20Base%20de%20dados%20%26%20Linguagem%20SQL/query_2.csv)
```sql
SELECT id,
	idade,
	limite_credito
FROM clientes
WHERE sexo = 'M'
ORDER BY idade DESC;
```

#### [**2.3. Query 3**](https://github.com/marciolws/Exercicios-SQL-para-Analise-de-Dados-EBAC/blob/main/Módulo%201%20-%20Base%20de%20dados%20%26%20Linguagem%20SQL/query_3.csv)
```sql
SELECT sexo,
	AVG(idade) AS "media_idade_por_sexo"
FROM clientes
GROUP BY sexo;
```

