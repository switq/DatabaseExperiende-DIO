**COOMANDOS SQL**

- **show** databases;
- **show** schemas;
- **drop** database _NomeDB_;
- **drop** database _NomeSC_;
- **create** database if not exists _NomeDB_;
- **use** database _NomeDB_;vv
    - **show** tables;
    - **desc** _atributo_;v
    - **CREATE TABLE** _person(_
	    _person_id smallint unsigned ,_
	    _fname varchar(20),_\
        _lname varchar(20),_\
        _gender enum('M','F'),_\
        _birth_date DATE,_\
        _street varchar(20),_\
        _city varchar(20),_\
        _state varchar(20),_\
        _country varchar(20),_\
        _postal_code varchar(20),_\
        constraint _pk_pers on_ primary key _(person_id)_\
    );
    - **create table** _favorite_food_(
	_person_id_ smallint unsigned,
    _food_ varchar(20),
    **constraint** _pk_favorite_food_ primary key (person_id, food),
    **constraint** _fk_favorite_food_person_id_ foreign key (_person_id_) references _person_(_person_id_)
    );
    - **select _*_ from** information_schema.table_constraints
    **where** constraint_schema = '_first_example_';
    - **insert into** person **values** ('1','Guilherme','Silva','M','2003-10-01','Rua Mamede','São Paulo','SP','Brasil','05788-430'),
    ('2','Giovanna','Silva','F','2003-10-01','Rua Mamede','São Paulo','SP','Brasil','05788-430');
    - **select** _*_ **from** person;

    - **delete from** person **where** person_id = 3 or person_id = 4;

    - **insert** into favorite_food values (1,'Paçoca'), (2,'Mato');


- **Contraints**
    - **select** * **from** information_schema.table_constraints
	where constraint_schema = 'company';
    - **select** * **from** information_schema.referential_constraints
	where constraint_schema = 'company';
    
    - **constraint** chk_salary_employee **check** (salary> 2000.0),
    - **constraint** pk_employee **primary key** (Ssn)

- **alter table** 
    - **drop column** _coluna_deletada_
    - **drop constraint** _constraint_deletada_
    - **add** _atributo_adic_ char(9) not null 
    - **on update cascade**

    - alter table employee
	    add constraint fk_employee\
        foreign key(Super_ssn) references employee(Ssn)\
        on delete set null\
        on update cascade;

- **Inserção de dados**
    - **insert into** employee **values** ('John', '0', 'Smith', '1965-01-09', '731-Fondren-Houston-TX', 'M', 30000, null, 5);

- **Recuperando dados com Queries**
    - select * from employee
    - select Ssn, Fname, Dname from employee e, departament d where (e.Ssn = d.Mgr_ssn)
    - select Ssn, Dependent_name, Relationship from employee, dependent where Essn = Ssn;
    - select Fname, Lname, Address from employee, department
	where Dname = 'Research' and Dnumber = Dno;
    - select Pname, Essn, Fname, Hours from employee, project, works_on 
        where Pnumber = Pno and Essn = Ssn;
    -select D.Dname, Dl.Dnumber, Dl.Dlocation 
        from department as D, dept_locations as Dl 
        where D.Dnumber = Dl.Dnumber;
    - select concat(Fname, ' ',Lname) as Employee from employee;