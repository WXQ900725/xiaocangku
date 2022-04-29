### 一、链服务新增 ddc-data-push.jar

### 二、配置文件新增

```
# mybatis
mybatis:
  mapper-locations: classpath:com/reddate/ddc/dao/*.xml
  config-location: classpath:mybatis-config.xml
  type-aliases-package: com.reddate.ddc.dao
  
  
# mysql
mysql:
  master:
    password: 123456
    url: jdbc:mysql://192.168.1.176:3306/bsn_ddc?characterEncoding=UTF-8&useSSL=false&serverTimezone=Asia/Shanghai
    username: root
  slave:
    password: 123456
    url: jdbc:mysql://192.168.1.176:3306/bsn_ddc?characterEncoding=UTF-8&useSSL=false&serverTimezone=Asia/Shanghai
    username: root
spring:
  main:
    allow-bean-definition-overriding: true
  shardingsphere:
    datasource:
      master:
        driver-class-name: com.mysql.cj.jdbc.Driver
        password: ${mysql.master.password}
        type: com.alibaba.druid.pool.DruidDataSource
        url: ${mysql.master.url}
        username: ${mysql.master.username}
      names: master,slave
      slave:
        driver-class-name: com.mysql.cj.jdbc.Driver
        password: ${mysql.slave.password}
        type: com.alibaba.druid.pool.DruidDataSource
        url: ${mysql.slave.url}
        username: ${mysql.slave.username}
    masterslave:
      load-balance-algorithm-type: round_robin
      master-data-source-name: master
      name: dataSource
      slave-data-source-names: slave
    props:
      sql:
        show: false
```

### 三、pom 新增

```
 <!--data push-->
        <dependency>
            <groupId>com.reddate.ddc</groupId>
            <artifactId>ddc</artifactId>
            <version>1.0-SNAPSHOT</version>
            <scope>system</scope>
            <systemPath>${basedir}/lib/ddc-data-push.jar</systemPath>
        </dependency>
        <dependency>
            <groupId>org.mybatis.spring.boot</groupId>
            <artifactId>mybatis-spring-boot-starter</artifactId>
            <version>2.2.0</version>

        </dependency>
        <dependency>
            <groupId>com.alibaba</groupId>
            <artifactId>druid</artifactId>
            <version>1.2.8</version>
        </dependency>
        <dependency>
            <groupId>mysql</groupId>
            <artifactId>mysql-connector-java</artifactId>
            <version>8.0.25</version>
        </dependency>
        <dependency>
            <groupId>org.apache.shardingsphere</groupId>
            <artifactId>sharding-jdbc-spring-boot-starter</artifactId>
            <version>4.1.1</version>

        </dependency>
```



### 四、其他改动参考武汉链：src/main/java/com/reddate/ddc/chain/service/EventTaskService.java  这个文件的改动就行

