create database bookmyshow;
use bookmyshow;
-- drop database db1;
show databases;

create table movies(
movie_id int primary key auto_increment,
movie_name varchar(50)not null,
duration int not null ,
language varchar(30) not null
);

create table theatres(
theatre_id int primary key auto_increment,
theatre_name varchar(30) not null,
location varchar(50)not null
);

create table shows(
show_id int primary key auto_increment,
movie_id int not null,
theatre_id int not null,
show_date date not null,
show_time time not null,
foreign key(movie_id) references movies(movie_id) on delete	cascade,
foreign key(theatre_id) references theatres(theatre_id) on delete cascade
);

show tables;

select * from movies;
select * from theatres;
select * from shows;
-- truncate table movies;
-- truncate table theatres;
-- truncate table shows;

-- drop table shows;

-- SET SQL_SAFE_UPDATES = 0;

insert into movies values (null,'movie1',120,'hindi');
insert into movies values (null,'movie2',125,'mal');
insert into movies values (null,'movie3',135,'hindi');
insert into movies values (null,'movie4',140,'tamil');
insert into movies values (null,'movie5',155,'mal');

insert into theatres values (null, 'theatre1','bangalore');
insert into theatres values (null, 'theatre2','mysore');
insert into theatres values (null, 'theatre3','kochi');
insert into theatres values (null, 'theatre4','mumbai');
insert into theatres values (null, 'theatre5','delhi');

insert into shows values(null,1,1,'2025-03-19','14:30:00');
insert into shows values(null,1,2,'2025-03-19','17:30:00');
insert into shows values(null,2,1,'2025-03-19','14:30:00');
insert into shows values(null,2,3,'2025-03-20','16:30:00');
insert into shows values(null,3,5,'2025-03-21','15:00:00');
insert into shows values(null,3,2,'2025-03-19','12:00:00');
insert into shows values(null,4,2,'2025-03-19','18:00:00');


select s.show_id, m.movie_name, t.theatre_name, s.show_date, s.show_time
from shows s
join movies m on m.movie_id = s.movie_id
join theatres t on t.theatre_id = s.theatre_id
where t.theatre_name = 'theatre2'
and s.show_date = '2025-03-19';
