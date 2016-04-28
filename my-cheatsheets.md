#My Various Spreadsheets

##Spring Tool Suite (3.7.3 RELEASE)
----------
Run an application ([Spring boot](http://projects.spring.io/spring-boot/#quick-start) should be installed)

    mvn spring-boot:run

Build JAR/WAR package

    mvn clean package

Start Tomcat ([Apache Tomcat7 Maven Plugin](http://mvnrepository.com/artifact/org.apache.tomcat.maven/tomcat7-maven-plugin/2.2) required)

    mvn tomcat7:run

##JAVA
----------
simple way to display an array of string

    System.out.println(Arrays.toString(myStringArray));
