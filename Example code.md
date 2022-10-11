1. project-1.java

        package com.project1;

        import org.springframework.boot.SpringApplication;
        import org.springframework.boot.autoconfigure.SpringBootApplication;

        @SpringBootApplication
        public class SimpleProjectApplication {

          public static void main(String[] args) {
            SpringApplication.run(SimpleProjectApplication.class, args);
            System.out.print("Hey this is my first spring boot app");
          }
        }
        
2. application.properties

        spring.autoconfigure.exclude=org.springframework.boot.autoconfigure.jdbc.DataSourceAutoConfiguration  
        server.port=9090
        
   **exclude** helps prevent Spring Boot from loading autoconfig classes in the presence of multiple @EnableAutoConfiguration / @SpringBootApplication annotations.
   And, to manually configure new port we can use server.port option in properties file
   

3. project-1/pom.xml

        <dependency>
          <groupId>org.hibernate</groupId>
            <artifactId>hibernate-core</artifactId>
        </dependency>
