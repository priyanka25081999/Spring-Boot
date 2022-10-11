1. Main Java file

        package com.jpa.test;

        import org.springframework.boot.SpringApplication;
        import org.springframework.boot.autoconfigure.SpringBootApplication;
        import org.springframework.context.ApplicationContext;

        import com.jpa.test.dao.UserRepository;
        import com.jpa.test.entities.User;

        @SpringBootApplication
        public class JpaExampleApplication {

          public static void main(String[] args) {
            ApplicationContext context = SpringApplication.run(JpaExampleApplication.class, args);

            UserRepository userRepo = context.getBean(UserRepository.class);

            User user = new User();
            user.setName("Priyanka");
            user.setCity("Pune");

            User user1 = userRepo.save(user);
            System.out.println(user1);
          }

        }
        
2. Properties file:

        spring.datasource.name=test
        spring.datasource.username=root
        spring.datasource.url=jdbc:mysql://localhost:3306/test     # or spring.datasource.url=jdbc:mysql://localhost:3306/test?serverTimezone=UTC
        spring.datasource.driver-class-name=com.mysql.cj.jdbc.Driver
        spring.jpa.properties.hibernate.dialect=org.hibernate.dialect.MySQL55Dialect
     
3. User class file:

        package com.jpa.test.entities;

        import javax.persistence.Entity;
        import javax.persistence.GeneratedValue;
        import javax.persistence.GenerationType;
        import javax.persistence.Id;

        @Entity
        public class User {

          @Id
          @GeneratedValue(strategy = GenerationType.AUTO)
          private int id;
          private String name;
          private String city;

          public void setId(int id)
          {
            this.id = id;
          }
          public int getId()
          {
            return id;
          }

          public String getCity() {
            return city;
          }
          public void setCity(String city) {
            this.city = city;
          }

          public String getName() {
            return name;
          }
          public void setName(String name) {
            this.name = name;
          }

        }

4. UserRepository class file:

        package com.jpa.test.dao;

        import org.springframework.data.repository.CrudRepository;

        import com.jpa.test.entities.User;

        public interface UserRepository extends CrudRepository<User, Integer> {

        }
        
Also, create a table in mysql (here table name is test), and then run this as a "Java application".



