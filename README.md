# Group-By-manual-SQL-
A instrução é frequentemente usada com funções agregadas para agrupar o resultado definido por uma ou mais colunas.



## O SQL GROUP POR Declaração

Os grupos de declaração têm os mesmos valores em linhas sumárias, como "encontrar o número de clientes em cada país".`GROUP BY`

A instrução é frequentemente usada com funções agregadas (, , , , , ) para agrupar o resultado definido por uma ou mais colunas.`GROUP BY``COUNT()``MAX()``MIN()``SUM()``AVG()`

### GRUPO POR Sintaxe

SELECT *column_name(s)*
FROM *table_name*
WHERE *condition*
GROUP BY *column_name(s)
*ORDER BY *column_name(s);*

------

## Banco de dados de demonstração

Abaixo está uma seleção da tabela "Clientes" no banco de dados de amostras northwind:

| CustomerID | CustomerName                       | ContactName        | Address                       | City        | PostalCode | Country |
| :--------- | :--------------------------------- | :----------------- | :---------------------------- | :---------- | :--------- | :------ |
| 1          | Alfreds Futterkiste                | Maria Anders       | Obere Str. 57                 | Berlin      | 12209      | Germany |
| 2          | Ana Trujillo Emparedados y helados | Ana Trujillo       | Avda. de la Constitución 2222 | México D.F. | 05021      | Mexico  |
| 3          | Antonio Moreno Taquería            | Antonio Moreno     | Mataderos 2312                | México D.F. | 05023      | Mexico  |
| 4          | Around the Horn                    | Thomas Hardy       | 120 Hanover Sq.               | London      | WA1 1DP    | UK      |
| 5          | Berglunds snabbköp                 | Christina Berglund | Berguvsvägen 8                | Luleå       | S-958 22   | Sweden  |

------

## SQL GROUP POR Exemplos

A seguinte declaração SQL lista o número de clientes em cada país:

### Exemplo

SELECT COUNT(CustomerID), Country
FROM Customers
GROUP BY Country;

A seguinte declaração SQL lista o número de clientes em cada país, classificados de alto a baixo:

### Exemplo

SELECT COUNT(CustomerID), Country
FROM Customers
GROUP BY Country
ORDER BY COUNT(CustomerID) DESC;

------

## Banco de dados de demonstração

Abaixo está uma seleção da tabela "Ordens" no banco de dados de amostras northwind:

| OrderID | CustomerID | EmployeeID | OrderDate  | ShipperID |
| :------ | :--------- | :--------- | :--------- | :-------- |
| 10248   | 90         | 5          | 1996-07-04 | 3         |
| 10249   | 81         | 6          | 1996-07-05 | 1         |
| 10250   | 34         | 4          | 1996-07-08 | 2         |

E uma seleção da tabela "Shippers":

| ShipperID | ShipperName      |
| :-------- | :--------------- |
| 1         | Speedy Express   |
| 2         | United Package   |
| 3         | Federal Shipping |

------

## GRUPO POR COM EXEMPLO DE JOIN

A seguinte declaração SQL lista o número de pedidos enviados por cada entregador:

### Exemplo 1

SELECT Shippers.ShipperName, COUNT(Orders.OrderID) AS NumberOfOrders FROM Orders
LEFT JOIN Shippers ON Orders.ShipperID = Shippers.ShipperID
GROUP BY ShipperName;

**EXEMPLO 2**

**SELECT** tb_seller.name, **ROUND**(**CAST** (**SUM**(price * quantity) **AS** numeric), 2) **FROM** tb_sale **INNER JOIN** tb_seller **ON** tb_sale.seller_id = tb_seller.id **GROUP BY** tb_seller.nome

obs: gera um relatório informando o nome do vendedor e suas respectivas vendas somadas
