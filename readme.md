# Hibernate

1. Add Hibernate to build.gradle

2. Add @Entity and @Table to controller, @Id and @GeneratedValue to id
```java
    @Entity
    @Table(name = "customer")
    public class Customer {
        @Id
        @GeneratedValue(strategy = GenerationType.IDENTITY)
```

3. Delete CustomerService class. Add HibernateCustomerService 
```java
    @Service
    public class HibernateCustomerService implements ICustomerService {
    }
```

4. Add 2 file Appconfiguration and AppInit in a new configuration package. Remove 2 related config .xml files. Add Bean for HibernateCustomerService to @Autowired in Controller
```java
    @Autowired
    private ICustomerService customerService;
```

5. Remove <context-param> in web.xml

6. Check in build.gradle again: thymeleaf, thymeleaf layout dialect, spring mvc, mysql, hibernate, commons-fileupload (if upload file)

7. Add hibernate.conf.xml in /resources
```
    <?xml version="1.0" encoding="utf-8"?>
    <!DOCTYPE hibernate-configuration PUBLIC
            "-//Hibernate/Hibernate Configuration DTD 3.0//EN"
                    "http://hibernate.sourceforge.net/hibernate-configuration-3.0.dtd">
    <hibernate-configuration>
        <session-factory>
           <property name="hibernate.connection.driver_class">com.mysql.cj.jdbc.Driver</property>
           <property name="hibernate.connection.url">jdbc:mysql://localhost:3306/cms</property>
           <property name="hibernate.connection.username">root</property>
           <property name="hibernate.connection.password">123456</property>
           <property name="hibernate.dialect">org.hibernate.dialect.MySQL8Dialect</property>
           <property name="show_sql">true</property>
           <property name="hbm2ddl.auto">update</property>
           <mapping class="com.codegym.model.Customer"/>
        </session-factory>
    </hibernate-configuration>
```

8. Add SessionFactory and EntityManager. Change some method to work with Hibernate (check the file)
