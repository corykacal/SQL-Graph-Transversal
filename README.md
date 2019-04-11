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
insert into edges(a,b)
values
    (1,2),
    (1,3),
    (3,4),
    (4,5),
    (3,5);
```

We know the longest path without a cycle is 3. So we can use this select here to get all the paths
```sql
select e1.a as a, e1.b as b, e2.b as c, e3.b as d from edges e1 left join edges e2 on e1.b=e2.a left join edges e3 on e2.b=e3.a;
```
Notice a left join is used, This is so paths of all sizes, not just 3 edges, will be found.  

If we do an inner join then only the path 1->3->4->5 will be selected.
```sql
select e1.a as a, e1.b as b, e2.b as c, e3.b as d from edges e1 join edges e2 on e1.b=e2.a join edges e3 on e2.b=e3.a
```
