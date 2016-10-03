

关系行数据库，在我看来就是一个不可分解的域的集合，和这些集合建立的关系
- entity descirption
- entity relation


有许多可选择的方案，来建立一个数据集合的关系，为了选择一个最佳或，通用的形式，需要先介绍几个概念

- active domain
    某个时刻，关系的某个域的值集和能表示这个数据集合，而其他的域不行
    在那个时刻，我们就称这个域对应的值得集合为active domain
- primary key
    一个不冗余的域或者联合域，能唯一表示一个n-tuple的关系 
- foreign key
    在不同的集合中需要交叉引用相同关系或者不同关系的元素时，需要永外键
    域(s)在R中不是primary key，并且在S中是primary key
    foreign key的加入使得entity descirption不在清晰
- nonsimple domain
    域不在是原子的，他们本身就可以在表示成一个关系，比如当我们通过primary key找到
    一个ralation的时候，这个relation的作用域是一个值的集合


normal form
--------------

> normalization: nonsimple domain被原子化的过程
> 1. find top relation's primary key
> 2. expand each subrelation by insert top primary key, itself primary key is combination of
>   top and itself orginal primary key
> 3. remove top tree node
> 4. repeat the relatin from next level


redundancy and consistency
--------------

## operations on relations 

    `permutation` : if a permutation is applied on the cloumns of n-arr relations, the resulting
    relation is said to be a permutation of the given relation.

- create new relation
- n factorial permutations avaliable on a relation of n domain 

置换可以包含相同顺序和反序的


#### projection

    'projection' : select m clounms from a n-arr relation and move the duplication rows in the
    previous relation to generate result relation


#### join

    'join' : given relation R and S, Op(i)(R) = Op(j)(S) generate relation U(1, 2, ij, ..), so
    Op(1..i..)(U) = R and Op(1..j..)(U) = S

join是基于RS在某个(些)域上有相同的域，产生一个连接的关系U，产生的结果可能有多种

>   natural jion : scan each row of R, join with S to generate a new relation


#### composition

    'composition' : if there exists jion bettwen R and S, there may exists composition followed by
    R, S are pre-defined projected

组合的前提是可以连接的，结果就是去掉join中的连接域，并且没有重复的row，如R(a, b), S(b, c) -> U(a, c)


#### restriction

> subset of a relation is a relation, which is subset domain(or rows?) of origin relation

relation R' is generated from R by S where Op(1..k)(R') = Op(1..n)(S)

根据S中的域的值，从R中找到一个相等的row，然后放到新的R'


--------------------

## redundancy

这里讲的是关系的冗余性，不是存储集合的冗余性

    collection C is a set of operations on relations, eache operation from C can yields a `unique
    relation`(natural join is eligible, but join is not)

    a relation R is C-derivable from a set S of relations if, `there exists an sequence of operations
    from C for all time, yields R from members of S`

so, how to define redundancy??


#### strong redundancy

关系集合中，至少存在一个关系做projecion后，是其他关系作projection后的子集
我们可以直接从逻辑数据中或存储数据中，删除冗余的模式

#### weak redundancy

关系集合中，如果存在一个关系做projection后，不是其他关系作projection的子集，
但，是这些projections的一个join

弱冗余是为了用户交流的一种逻辑需求，他们不能直接从数据系统中被移除


--------------------

## consistency



















