# My Various Cheatsheets
----------

## Spring Tool Suite (3.7.3 RELEASE)
Run an application ([Spring boot](http://projects.spring.io/spring-boot/#quick-start) should be installed)

    mvn spring-boot:run

Build JAR/WAR package

    mvn clean package

Start Tomcat ([Apache Tomcat7 Maven Plugin](http://mvnrepository.com/artifact/org.apache.tomcat.maven/tomcat7-maven-plugin/2.2) required)

    mvn tomcat7:run

## JAVA
Simple way to display an array of string

    System.out.println(Arrays.toString(myStringArray));

## MAVEN
settings.xml file location (Debian based distros)

    /usr/share/maven/conf

Skip maven tests when packaging

    mvn package -Dmaven.test.skip=true

## Symfony (2.7)
Create an admin user

    php app/console fos:user:create admin admin@admin.dev admin

## NPM (3.9.2)
Install a npm module and save it to package.json

    npm install <module_name> --save

## Arch Linux (and derivatives)
Clean the package cache (to save space)

    sudo pacman -Sc

Reinstall grub2 (may work on other distributions)

    sudo grub-install --recheck --root-directory=/mnt /dev/sda\n
    sudo grub-mkconfig -o /mnt/boot/grub/grub.cfg

Remove a desktop environement (kde)

    pacman -Rnsc kde
    sudo pacman -Rnsc kde-applications # To remove the DE associated apps

Force quit pacman/yaourt

    sudo rm /var/lib/pacman/db.lck
    
## [Jekyll](https://jekyllrb.com/)
- Any file whose name starts with _ is not imported into the _site folder after "compiling".

## PostgreSQL
Connect to a database

    psql <dbName> <userName>

## Git
Change git default editor

    git config --global core.editor <editor>

Modify last commit

    git commit --amend

Create a .gitignore on windows (create the gitignore.txt file before)

    ren gitignore.txt .gitignore

Difference between --mixed, --soft, --hard reset (click on image to see source):

[![git reset different types](img/hard_soft_mixed.jpg)](http://stackoverflow.com/a/3528483/2300596)

[A very good GIT Cheatsheet](http://ndpsoftware.com/git-cheatsheet.html#loc=workspace;)

## VIM
Change color scheme (to elflord in this example) on the fly

    :colorscheme elflord
 
## Bash
[LeCoupa's BASH Cheatsheet](https://gist.github.com/LeCoupa/122b12050f5fb267e75f)

## Windows Command
Find the process using a specific port (8080)

    netstat -a -n -o | find "8080"
Kill a process by its PID  (2728)

    taskkill /F /PID 2728
