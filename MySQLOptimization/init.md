- `关于mysql表自增长的问题
当mysql设置表自增长的时候，比如id列，没加入一条id使用show create table tablename;会显示出当前的AUTO_INCREMENT=71，
有时候会出现自动增长的值，小于实际插入的值，这个时候就会报错了。
[Err] 1062 - Duplicate entry '70' for key 'PRIMARY'
执行sql:
alter table ztes AUTO_INCREMENT=52;
AUTO_INCREMENT的值随意填写就行，AUTO_INCREMENT会自动改成当前合适的值。
或出现这种情况的原因是因为在自增长序列的时候进行了update到高值的原因。这个时候AUTO_INCREMENT不会自动增长。故而出现这样的问题。所以需要禁止update自增长序列的操作。`