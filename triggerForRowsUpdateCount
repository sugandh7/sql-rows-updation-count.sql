create table test_data(a varchar(1));
insert into test_data values('A');
insert into test_data values('B');
insert into test_data values('C');
insert into test_data values('D');
select * from test_data;

 A
 B
 C
 D
create table noofchanges(data varchar(1),numberofchanges int) ;
insert into noofchanges(data,numberofchanges) select a,0 from test_data;
select * from noofchanges;

A   0
B   0
C   0
D   0


CREATE OR REPLACE TRIGGER test_data_before_update
BEFORE UPDATE
   ON test_data
   FOR EACH ROW
BEGIN
    update noofchanges 
    set numberofchanges=numberofchanges+1 
    where data=:old.a;    
END;


update test_data set a='A' where a='B';
select * from test_data;


 A 
 A
 C
 D

select * from noofchanges
A   0
B   1
C   0
