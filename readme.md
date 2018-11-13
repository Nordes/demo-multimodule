# Create multi project
Starter for Spring 5 + Api + Dynamic plugin (demo project)

Following the guide from: http://websystique.com/maven/creating-maven-multi-module-project-with-eclipse/?fbclid=IwAR2CIXUHUeVESvqkNSURb7rLufA3HNJw0TEVspVEIcjJ8S985U2BUoxXono

And then the following resource: https://howtodoinjava.com/maven/maven-parent-child-pom-example/

## Create the multi-project
```bash
> mvn archetype:generate "-DgroupId=com.honosoft.demo.multimodule" "-DartifactId=demo-multimodule"
> cd demo-multimodule
```

From there, you can delete the `src` folder. It won't be of any uses for us.

Edit the pom file and set the packaging to `pom`
```
  <packaging>pom</packaging>
```

## Create an API project (Data contract)
```bash
> mvn archetype:generate "-DgroupId=com.honosoft.demo.multimodule"  "-DartifactId=demo-multimodule-plugin-api"
```

Don't forget to edit the `pom` file and be sure it's a JAR packaging. And also that the parent is marked as a relative path (pom)
```xml
    <relativePath>../pom.xml</relativePath>
```

## Create one plugin
```bash
> mvn archetype:generate "-DgroupId=com.honosoft.demo.multimodule"  "-DartifactId=demo-multimodule-plugin-twitter"
```

## Create the MVC app
If not there you will have issue so please edit your settings.xml (maven folder)
```
    <profile>
      <id>spring-mvc-quickstart</id>

      <repositories>
        <repository>
          <id>spring</id>
          <url>http://kolorobot.github.io/spring-mvc-quickstart-archetype</url>
        </repository>
      </repositories>
    </profile>
```

After you can run this
```bash
> mvn archetype:generate `
        "-DarchetypeGroupId=pl.codeleak" `
        "-DarchetypeArtifactId=spring-mvc-quickstart" `
        "-DarchetypeVersion=5.0.0" `
        "-DgroupId=com.honosoft.demo.multimodule" `
        "-DartifactId=demo-multimodule-rest" `
        "-DarchetypeRepository=http://kolorobot.github.io/spring-mvc-quickstart-archetype" `
        "-Pspring-mvc-quickstart"
```

## To compile
`> mvn clean install`

## To package
`> mvn package` (From the project itself)

## To run tomcat
```bash
> mvn -pl demo-multimodule-rest tomcat7:run
```

Access your website at: [http://localhost:8080](http://localhost:8080)

# Author
Nordès Ménard-Lamarre

# License
MIT?