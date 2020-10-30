# Coisas de banco de dados que podem ser úteis.

## Acessar banco

```bash
docker run --rm -it postgres:latest psql postgres://$username:$password>@<adrresss>/<dbname>
```

```bash
psql -h <link-do-db> --username=<username> <nome-do-db>
```

## Trabalhando com json

### Setar um campo json
```sql
update "Table" set column_name = jsonb_set(user_data, '{user_id}', '1111111') 
where other_column = 'abcabca' and third_column = 'string';
```

### Selecionar atributos com campos json
```sql
SELECT count(*) FROM "TableName" 
WHERE column_name->>'attribute'='value';
```

## Navegar em campo json
```sql
--- pegar msgs da pessoa
select var_name.column_name -> 'attribute' -> 'other_attribute' -> 'more_attribute' from "TableName" var_name
where var_name.anoter_column = '12345' order by var_name.third_column
```

## Join
```sql
select var1.column_name->'attribute'->>'value', var1.column_name -> 'attribute' -> 'another_attirbute' -> 'more_attribute',
var2.another_column->>'another_value' , bm.more_column -> 'new_attribute' -> 'yet_another_attribute' from "Table1" var1 
inner join "Table2" var2 on var1.third_column = var2.more_column where var1.yes_other_column = '12345' order by im.criteria_column;
```

