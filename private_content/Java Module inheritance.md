
# Create Parent Module

`pom.xml`
```xml
<project  
        xmlns="http://maven.apache.org/POM/4.0.0"  
        xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"  
        xsi:schemaLocation="http://maven.apache.org/POM/4.0.0 http://maven.apache.org/maven-v4_0_0.xsd">  
  
  <modelVersion>4.0.0</modelVersion>  
  <groupId>com.mycompany</groupId>  
  <artifactId>MyCompanyProject</artifactId>  
  <version>1.0-SNAPSHOT</version>  
  <packaging>pom</packaging>

  <!-- Children modules -->
  <modules>  
    <module>ConsoleApp</module>  
    <module>SharedLibrary</module>  
  </modules>
  <!-- Children modules -->
  
  <properties>  
    <maven.compiler.source>21</maven.compiler.source>  
    <maven.compiler.target>21</maven.compiler.target>  
  </properties>  
  
  <build>  
    <plugins>  
      <plugin>  
        <groupId>org.apache.maven.plugins</groupId>  
        <artifactId>maven-jar-plugin</artifactId>  
        <version>3.1.0</version>  
        <configuration>  
          <archive>
	        <!-- Set Main class -->
            <manifest>  
              <addClasspath>true</addClasspath>  
              <mainClass>com.mycompany.App</mainClass>  
            </manifest>
            <!-- Set Main class -->
		    
		    <!-- Path to build -->
            <manifestEntries>  
              <Class-Path>lib/</Class-Path>  
            </manifestEntries>
            <!-- Path to build -->
          </archive>  
        </configuration>  
      </plugin>  
    </plugins>  
  </build>  
</project>
```

# Create `SharedLibrary` Children Module

`pom.xml`
```xml
<project  
        xmlns="http://maven.apache.org/POM/4.0.0"  
        xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"  
        xsi:schemaLocation="http://maven.apache.org/POM/4.0.0 http://maven.apache.org/xsd/maven-4.0.0.xsd">  
    <modelVersion>4.0.0</modelVersion>  
    <parent>  
        <groupId>com.mycompany</groupId>  
        <artifactId>MyCompanyProject</artifactId>  
        <version>1.0-SNAPSHOT</version>  
    </parent>  
  
    <artifactId>SharedLibrary</artifactId>  
    <packaging>jar</packaging>  
    <version>1.0-SNAPSHOT</version>  
  
    <properties>  
        <maven.compiler.source>21</maven.compiler.source>  
        <maven.compiler.target>21</maven.compiler.target>  
    </properties>  
  
  
    <build>  
        <plugins>  
            <plugin>  
                <groupId>org.apache.maven.plugins</groupId>  
                <artifactId>maven-jar-plugin</artifactId>  
                <configuration>  
                    <archive>  
                        <manifest>  
                            <addClasspath>true</addClasspath>  
                            <mainClass>com.mycompany.Test</mainClass>  
                        </manifest>  
                    </archive>  
                    <outputDirectory>../libs</outputDirectory>  
                </configuration>  
            </plugin>  
        </plugins>  
    </build>  
  
</project>
```

# Create `ConsoleApp` Children Module

`pom.xml`
```xml
<project xmlns="http://maven.apache.org/POM/4.0.0" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"  
         xsi:schemaLocation="http://maven.apache.org/POM/4.0.0 http://maven.apache.org/maven-v4_0_0.xsd">  
    <modelVersion>4.0.0</modelVersion>  
    <parent>  
        <groupId>com.mycompany</groupId>  
        <artifactId>MyCompanyProject</artifactId>  
        <version>1.0-SNAPSHOT</version>  
    </parent>  
  
    <artifactId>ConsoleApp</artifactId>  
    <packaging>jar</packaging>
  
    <properties>  
        <maven.compiler.source>21</maven.compiler.source>  
        <maven.compiler.target>21</maven.compiler.target>  
    </properties>  
  
    <build>  
        <plugins>  
            <plugin>  
                <groupId>org.apache.maven.plugins</groupId>  
                <artifactId>maven-jar-plugin</artifactId>  
                <configuration>  
                    <outputDirectory>../libs</outputDirectory>  
                </configuration>  
            </plugin>  
        </plugins>  
    </build>
  
    <dependencies>  
        <dependency>  
            <groupId>com.mycompany</groupId>  
            <artifactId>SharedLibrary</artifactId>  
            <version>1.0-SNAPSHOT</version>  
        </dependency>  
    </dependencies>  
  
</project>
```

# Compile project

```bash
mvn clean install
```
# Run project

```bash
java -cp libs/SharedLibrary-1.0-SNAPSHOT.jar:libs/ConsoleApp-1.0-SNAPSHOT.jar com.mycompany.App
```

> [!IMPORTANT]  
> In parent project folder!