JPA
===================


JPA는  관계형 데이터베이스에 접근하기 위한 표준 ORM 기술을 제공하며, DB에 접근하기 위해 사용되었던 Entity Bean을 대체하는 기술로 Native Query를 지원한다.

---------------

### <i class="icon-file"></i>Native Query

Native Query는 Session에서 Connection을 가져와 POJO에서 사용하는것 처럼 직접 Query를 작성하여 사용하는 방식이다.

> **@Entity Class 생성**

> - @Table : 사용할 테이블명
- @NamedQuery(name="사용할 Query문의 이름(대체 명)", qeury="쿼리문")
- @JoinTable(name="ORDERAPP_ORDERS2ITEMS")
 @JoinColumn(name = "user_id")
- @Column(name = "name", nullable = false)
- @OneToOne, 1:1 관계 매핑
	  @OneToMany / @ManyToOne, 1:N / N:1 관계 매핑
	  @ManyToMany, N:M 관계 매핑
	 >> <i class="icon-pencil"></i>**example** 
	 @OneToMany(mappedBy="customer", cascade={CascadeType.PERSIST, CascadeType.REMOVE})
	      @ManyToOne(fetch=FetchType.LAZY, optional=false)
	  - mappedBy : 종속관계를 보여준다. 부모가 되는 Clssd명을 적는다.
	  - CascadeType 
	   - CascadeType.RESIST
	       : 엔티티를 생성하고, 연관 엔티티를 추가하였을 때 persist() 를 수행하면 연관 엔티티
	     도 함께 persist()가 수행된다.  만약 연관 엔티티가 DB에 등록된 키값을 가지고 있다면 detached entity passed to persist Exception이 발생한다.
       - CascadeType.MERGE
        : 트랜잭션이 종료되고 detach 상태에서 연관 엔티티를 추가하거나 변경된 이후에 부모 엔티티가 merge()를 수행하게 되면 변경사항이 적용된다.(연관 엔티티의 추가 및 수정 모두 반영됨)
       - CascadeType.REMOVE : 삭제 시 연관된 엔티티도 같이 삭제됨
       - CascadeType.DETACH
        : 부모 엔티티가 detach()를 수행하게 되면, 연관된 엔티티도 detach() 상태가 되어 변경사항이 반영되지 않는다.
       - CascadeType.ALL : 모든 Cascade 적용
	  - fetch 
	   : 연관을 맺고 있는 Entity들을 요청하는 순간 가져오는 설정이 LAZY 며,
	   해당 Entity를 가져올 때 미리 연관을 맺고 있는 Entity들까지 모두 가져오는 것이 EAGER 이다.
	   



MariaDB
===================

MariaDB는 MySQL과 동일한 소스 코드를 기반으로 한 오픈 소스의 관계형 데이터베이스 관리 시스템(RDBMS)이다.

---------------

#### <i class="icon-file"></i>사용 방법
 - 사용자 추가. 
MariaDB [(none)]> create user 'utime'@'localhost' identified by '*p*a*s*s*w*o*r*d*';
Query OK, 0 rows affected (0.00 sec)
 
 - 권한 변경 
MariaDB [(none)]> grant all privileges on *.* to 'utime'@'localhost';
Query OK, 0 rows affected (0.00 sec)
 
 - 위 권한이 외부 서버에서 접근이 안될경우
GRANT ALL PRIVILEGES ON *.* TO <계정이름>@'%' IDENTIFIED BY '<암호>';

 - 사용자 설정 적용 
MariaDB [(none)]> flush privileges;
Query OK, 0 rows affected (0.00 sec)
 
 - 데이터 베이스 추가. 
MariaDB [(none)]> create database utimeDB;
Query OK, 1 row affected (0.00 sec)
 
 
 - 생성된 데이터 베이스 확인 
MariaDB [(none)]> show databases;
+--------------------+
| Database           |
+--------------------+
| information_schema |
| mysql              |
| performance_schema |
| test               |
| utimedb            |
+--------------------+
5 rows in set (0.00 sec)
 
 - 데이터 베이스 사용.
MariaDB [(none)]> use utimedb;

 - 추가된 테이블 확인 
MariaDB [utimedb]> show tables;

 - 인덱스 작업 추가. 
MariaDB [utimedb]> create index roadconditionindex on roadcondition (datekey, roadsectionid);
Query OK, 0 rows affected (0.05 sec)
Records: 0  Duplicates: 0  Warnings: 0
 
추가된 인덱스 보기 
MariaDB [utimedb]> show index from roadcondition;



#### <i class="icon-pencil"></i>flush privileges
 flush privileges 는 grant 테이블을 reload 함으로 변경사항을 바로 적용해주는 명령어이다. INSERT, UPDATE와 같은 SQL문이 아닌 grant 명령어를 사용해서 사용자를 추가하거나 권한등을 변경하였다면 굳이 실행할 필요가 없다.

