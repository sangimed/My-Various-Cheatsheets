# My-Various-Cheatsheets
## Spring
Run an application ([Spring boot](http://projects.spring.io/spring-boot/#quick-start) should be installed)

    mvn spring-boot:run

Build JAR/WAR package

    mvn clean package

Start Tomcat ([Apache Tomcat7 Maven Plugin](http://mvnrepository.com/artifact/org.apache.tomcat.maven/tomcat7-maven-plugin/2.2) required)

    mvn tomcat7:run

## JAVA
Generic way of overriding Object.toString() method (thank you org.apache.commons.lang3)

```java
@Override
public String toString() {
    return ToStringBuilder.reflectionToString(this, ToStringStyle.SHORT_PREFIX_STYLE);
}
```

Call plsql procedure from java with JPA

```java
@PersistenceContext
private EntityManager entityManager;

public String myfunc(final String param) {
    StoredProcedureQuery query = entityManager.createStoredProcedureQuery("plsql_procedure_name")
            .registerStoredProcedureParameter("param", String.class, ParameterMode.IN)
            .registerStoredProcedureParameter("result", String.class, ParameterMode.OUT)
            .setParameter("param", param);

    query.execute();

    return (String) query.getOutputParameterValue("result");

}
```

## JS/TS/Node

### JS 

* [ES6 Overview in 350 Bullet Points](https://ponyfoo.com/articles/es6)

* Will evaluate to true if aVariable is not : null, undefined, NaN, "", 0, false.

        if( aVariable ) {
         // Stuff
        }

### Node

Get the current global prefix
```
npm prefix -g
```

### NestJs

File uploading
```Typescript
  @Post('upload')
  @UseInterceptors(FileInterceptor('file',
    {
      storage: diskStorage({
        destination: './uploads', // be sure to create a .gitignore that ignores everything in the folder (except itself)

        filename: (req, file, cb) => {
          const randomName = Array(32).fill(null).map(() => (Math.round(Math.random() * 16)).toString(16)).join('')
          return cb(null, `${file.originalname}`)
        }
      })
    }
  ))
  async upload(@UploadedFile() file: BufferedFile) { // BufferedFile is an interface defined in the project
    await this.fileService.upload(file);
  }
```

## MAVEN
settings.xml file location (Debian based distros)

    /usr/share/maven/conf

Skip maven tests when packaging

    mvn package -DskipTests

Put a jar in the local repository
```
   mvn install:install-file
  -Dfile=<path-to-file>
  -DgroupId=<group-id>
  -DartifactId=<artifact-id>
  -Dversion=<version>
  -Dpackaging=<packaging>
  -DgeneratePom=true
 
Where: <path-to-file>  the path to the file to load
       <group-id>      the group that the file should be registered under
       <artifact-id>   the artifact name for the file
       <version>       the version of the file
       <packaging>     the packaging of the file e.g. jar
```
## Symfony (2.7)
Create an admin user

    php app/console fos:user:create admin admin@admin.dev admin

## NPM (3.9.2)
Install a npm module and save it to package.json

    npm install <module_name> --save

## Linux

Do nothing when the lid is closed (useful when using a laptop as a server)

```ini
# Content of /etc/systemd/logind.conf
[Login]
HandleLidSwitch=ignore
```
List all systemd services (grepable)
    
    # systemctl list-units --type=service --state=active
    OR
    # systemctl --type=service --state=active

Copy a file over SSH
    
    ssh-copy-id -i <file_path> <user@host>
    
Ping a specific port
 
    nc -vz {host} {port}
    
Copy Content of a folder to another folder [src](https://askubuntu.com/a/86891/116825)

    cp -a /source/. /dest/
    
Delete the content of a folder
    
     rm -rfv folder/*

copy folder

    cp -ar source destination/ # -a preseves ownership -r for recursivity

### Arch Linux (and derivatives)

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

## Red Hat (based) distros
~~go to the internetz ! (uses /!\ Google Public DNS /!\)~~
- Spot the disconnected network interface with `nmcli`.
- Then edit the right config file `sudo vi /etc/sysconfig/network-scripts/ifcfg-<interface-name>` by changing `ONBOOT=no` to `ONBOOT=yes`*
- Restart the network service `sudo systemctl restart network.service`
- Test `ping google.com`


## [Jekyll](https://jekyllrb.com/)
- Any file whose name starts with _ is not imported into the _site folder after "compiling".

## PostgreSQL
Connect to a database

    psql <dbName> <userName>
    
List all reserved words
    
    select * from pg_get_keywords()

## Git
Reverse git log

    git log --reverse

Change git default editor

    git config --global core.editor <editor>

Modify last commit

    git commit --amend

Create a .gitignore on windows (create the gitignore.txt file before)

    ren gitignore.txt .gitignore

Difference between --mixed, --soft, --hard reset (click on image to see source):

[![git reset different types](img/hard_soft_mixed.jpg)](http://stackoverflow.com/a/3528483/2300596)

[A very good GIT Cheatsheet](http://ndpsoftware.com/git-cheatsheet.html#loc=workspace;)

Change git remote URL (for remote repository migration)

    git remote set-url origin git://new.url.here

Add multiple remotes (to push to both a gitlab and a github server for example)

    git remote set-url origin --push --add <a remote>
    git remote set-url origin --push --add <another remote>

[Fast forwarding](https://sandofsky.com/images/fast_forward.pdf)

Ignoring a file locally

    git update-index --skip-worktree path/to/file
    
    # Confirm
    git ls-files -v | grep ^S
    
    # Restore
    git update-index --no-skip-worktree path/to/file
    
Global settings for line endings

    $ git config --global core.autocrlf true
    
Squashing
- https://medium.com/@slamflipstrom/a-beginners-guide-to-squashing-commits-with-git-rebase-8185cf6e62ec

Cleaning untracked files
    
    # Perform a “dry run” and show you what files and directories will be deleted
    git clean -d -n
    
    # Actual cleaning
    git clean -d -f
    
Reset creds

    git config --system --unset credential.helper

## VIM

```bash
# Change color scheme (to elflord in this example) on the fly
:colorscheme elflord

# Display line numbers
:set number

# Delete current line
dd # or D

# Delete a single word
dw

# Delete all content
%d
```

## Bash
[LeCoupa's BASH Cheatsheet](https://gist.github.com/LeCoupa/122b12050f5fb267e75f)

## Windows Commands
Find the process using a specific port (8080)

    netstat -a -n -o | find "8080"

Get the name of a process from its PID

    tasklist /fi "pid eq 21385"

Kill a process by its PID  (2728)

    taskkill /F /PID 2728

Display the command line with which the process is launched

    wmic process where processid=<pid> get commandline

## LaTeX
A good looking listing configuration

     \lstset{aboveskip=20pt}
     
     \begin{lstlisting}[firstnumber=1,numbers=left,numberstyle=\bf \tiny \color{black},caption={Hello World},language=pascal,frame=lines]
        CODE HERE ...
    \end{lstlisting}


## RegExp
Select all the lines containing "hello"

    ^.*hello.*\r\n

## WireShark

    http contains "text" or http.response.code == 200

## Tomcat
Undeploy an app via tomcat manager

    curl -u user:pwd  "http://localhost:port/manager/text/undeploy?path=/myappspath/&version=myappsversion"

## Intellij

### Usual Intellij problems and how to resolve them

    Error:java: javacTask: source release 8 requires target release 1.8

Reimporting all maven projects resolves this (<kbd>CTRL</kbd>+<kbd>SHIFT</kbd>+<kbd>A</kbd> then search for `reimport`).

## Docker

- `docker-compose.yml` describes a docker based application (could use different containers).

Docker interactive mode
    
    docker container run -ti ubuntu bash

## Miscellaneous

 - [Music for programming - https://musicforprogramming.net](https://musicforprogramming.net/)
 - :warning: https://github.com/sangimed/Coding-rules :warning:
