SQLscripts.md

-1-
create table PurchaseOrder (
	Id int not null primary key identity (1,1),
	PurchasedDate datetime not null,
	VendorId int not null foreign key references Vendor(Id)
)

insert PurchaseOrder (PurchasedDate, VendorId) 
	Values
	('2017-08-29', 1)

select * from PurchaseOrder

-2-
/*
create table vendor (
	Id int not null primary key identity (1,1),
	Name nvarchar (50) not null,
)
*/
--insert into Vendor (Name) values ('Amazon')

Select * from Vendor

delete from vendor where id = 1

-3-
--join views
select PurchaseOrder.Id, PurchasedDate, Name as 'Vendor' 
	from PurchaseOrder
	join vendor 
		on PurchaseOrder.VendorId = Vendor.Id

************************************************************
-1-
create table Major (
	Id int not null primary key identity (1,1),
	Description nvarchar (50) not null
)

insert into major (description) values ('Audiology') 
insert into major (description) values ('Biology')
insert into major (description) values ('Linguistics')
insert into major (description) values ('CS')
insert into major (description) values ('ME')
insert into major (description) values ('IPS')

select * from major

-2-
Alter table Student
	add MajorId int not null 

insert into student (FirstName, LastName, Address, City, State,
Zipcode, PhoneNumber, Email, Birthday, MajorId) values
('Bobby', 'Doud', '123 Any Street', 'Loveland', 'OH', '45140', 
'5135551212', 'bdoud@maxtrain.com', '2017-12-09', 5)

select * from student 

-3-
select major.description as 'Major', 
concat (student.firstname, ' ', student.lastname) as 'Full Name'
	from major
	join student
		on student.majorid = major.id
	order by major.description

