#### Spring Boot devtools介绍

1. 主要作用

   监控程序变化，自动重新启动。

2. 原理

   使用了两个ClassLoader，一个ClassLoader加载那些不会改变的类（第三方jar包），另一个加载那些会改变的类，被称为restart ClassLoader，在有代码更改的时候，原先那个restart ClassLoader被抛弃，重新创建一个restart ClassLoader，由于需要加载的类相对较少（没有第三方jar包），所以可以实现快速的重启。

3. 使用

   ```
   <dependency>
       <groupId>org.springframework.boot</groupId>
       <artifactId>spring-boot-devtools</artifactId>
       <optional>true</optional>
   </dependency>
   ```

   devtools配置：

   - 在application.properties中配置`spring.devtools.restart.enabled=false`，此时restart类加载器还会初始化，但是不会监听文件的变化，如需完全关闭热加载，需要在`SpringApplication.run()`之前设置`System.setProperty(“spring.devtools.restart.enabled”, “false”);`

     ```java
     @SpringBootApplication
     public class ToolsApplication {
     
         public static void main(String[] args) {
             System.setProperty("spring.devtools.restart.enabled", "false");
             SpringApplication.run(ToolsApplication.class, args);
         }
     
     }
     ```

   - 配置文件

     ```java
     #热部署生效
     spring.devtools.restart.enabled: true
     #设置重启的目录
     #spring.devtools.restart.additional-paths: src/main/java
     #classpath目录下的WEB-INF文件夹内容修改不重启
     spring.devtools.restart.exclude: WEB-INF/**
     ```

   IDEA配置：

   - 当我们修改了类之后，idea默认是不会进行自动编译的，而devtools是通过监听calsspath下的文件来进行监听的，所以我们需要打开idea的自定编译功能
     1. File-Settings-Compiler-Build Project automatically
     2. ctrl + shift + alt + /,选择Registry,勾上 Compiler autoMake allow when app running

4. 说明

   - 设置`<optional>true</optional>`之后，使用spring boot插件打包时，默认不会包含devtools。
   - devtools可以实现页面热部署，但这个直接通过设置`spring.thymeleaf.cache=false`也可以实现。
   - 同时可以实现类文件更改热部署，配置文件更改热部署。
   - 这里的热启动（类文件更改）属于项目重启，会清空session中的值。
   - 默认情况下，/META-INF/maven，/META-INF/resources，/resources，/static，/templates，/public这些文件夹下的文件发生变动之后不会使应用重启，但是会重新加载（devtools内嵌了一个LiveReload server，当资源发生更改是，刷新浏览器）

