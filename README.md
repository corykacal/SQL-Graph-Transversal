# Graph transversal in SQL  

### basic graph creation
First, we will have just the edges. There is no need for node tables at the moment.
```sql
create table edges(
	a smallint,
	b smallint
);
```
We will now populate this table with the values based on this graph.

![alt text](https://github.com/corykacal/SQL-Graph-Transversal/blob/master/images/graph1.png?raw=true)

```sql
select e1.a as a, e1.b as b, e2.b as c from edges e1 left join edges e2 on e1.b=e2.a
```
