###Profile

利用多个profile分离开发、测试和产品环境：

```
<project>
  <profiles>
    <profile>
      <id>development</id>
      <activation>
        <activeByDefault>true</activeByDefault>
      </activation>
      <build>
        <filters>
          <filter>profile-development.properties</filter>
        </filters>
      </build>
    </profile>
    <profile>
      <id>production</id>
      <build>
        <filters>
          <filter>profile-production.properties</filter>
        </filters>
      </build>
    </profile>
  </profiles>
</project>
```

###Filter功能

来自于Maven Resource Plugin，利用项目属性或者系统属性的值来替代项目资源文件的值（比如properties、xml文件等）：

+ -Duser.name=foo
+ ${user.name}将会被替换为foo

```xml
<project>
  <build>
    <resources>
      <directory>src/main/resource</directory>
      <filtering>true</filtering>
    </resources>
  </build>
</project>
```

+ 利用项目里的属性值

```xml
<project>
  <properties>
    <user.name>foo</user>
    <user.email>foo@bar.com</user>
  </properties>
</project>
```

```xml
<project>
  <build>
    <filters>
      <filter>project.properties</filter>
    </filters>
  </build>
</project>
```
