# Spring Boot配置Fast Json

## 一、说明

Spring Boot默认的JSON转换器是Jackson，如果项目中需要使用fastjosn作为默认的JSON转换器，则需要进行配置，更改默认的转换器。

## 二、使用：

- pom文件中引入依赖

  ```java
  <dependency>
  	<groupId>com.alibaba</groupId>
  	<artifactId>fastjson</artifactId>
  	<version>1.2.46</version>
  </dependency>
  ```

- 通过Bean方式注入

  ```java
  @SpringBootApplication
  public class ToolsApplication {
  
      /**
       * @Description: 配置springboot的默认JSON转换器为fast json
       * @param:
       * @return:
       * @author: Matt
       * @date: 2020/1/16 15:48
       */
      @Bean
      public HttpMessageConverters fastJsonHttpMessageConverters() {
          // 1.定义一个converters转换消息的对象
          FastJsonHttpMessageConverter fastConverter = new FastJsonHttpMessageConverter();
          // 2.添加fast json的配置信息，比如: 是否需要格式化返回的json数据
          FastJsonConfig fastJsonConfig = new FastJsonConfig();
          fastJsonConfig.setSerializerFeatures(SerializerFeature.PrettyFormat);
          // 3.在converter中添加配置信息
          fastConverter.setFastJsonConfig(fastJsonConfig);
          // 4.将converter赋值给HttpMessageConverter
          HttpMessageConverter<?> converter = fastConverter;
          // 5.返回HttpMessageConverters对象
          return new HttpMessageConverters(converter);
      }
  
      public static void main(String[] args) {
          SpringApplication.run(ToolsApplication.class, args);
      }
  
  }
  ```

  