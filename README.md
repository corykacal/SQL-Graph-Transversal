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

<Graph indexType="custom" height="400" width="400" nodes={[{label:"1",center:{x:60,y:310.2}},{label:"2",center:{x:60,y:102.1}},{label:"3",center:{x:241.8,y:391}},{label:"4",center:{x:239.6,y:168.8}},{label:"5",center:{x:401.5,y:275.2}}]} edges={[{source:0,target:1},{source:0,target:2},{source:2,target:3},{source:2,target:4},{source:3,target:4}]} />

```sql
select e1.a as a, e1.b as b, e2.b as c from edges e1 left join edges e2 on e1.b=e2.a
```
