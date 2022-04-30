## 添加依赖

```xml
<dependency>
    <groupId>com.zaxxer</groupId>
    <artifactId>HikariCP</artifactId>
    <version>3.4.5</version>
</dependency>

<dependency>
    <groupId>mysql</groupId>
    <artifactId>mysql-connector-java</artifactId>
    <version>8.0.20</version>
</dependency>
```



## 示例代码

```java
import com.zaxxer.hikari.HikariConfig;
import com.zaxxer.hikari.HikariDataSource;

import java.sql.*;

public class HikariDemo {

    // 数据库账号密码等信息
    private static final String URL = "jdbc:mysql://localhost:3306/blog?serverTimezone=Asia/Shanghai";
    private static final String USERNAME = "root";
    private static final String PASSWORD = "123456";
    private static final String Driver = "com.mysql.cj.jdbc.Driver";

    public static void main(String[] args) {

        // 配置文件
        HikariConfig hikariConfig = new HikariConfig();
        hikariConfig.setJdbcUrl(URL);  // mysql

        hikariConfig.setDriverClassName(Driver);
        hikariConfig.setUsername(USERNAME);
        hikariConfig.setPassword(PASSWORD);
        hikariConfig.addDataSourceProperty("cachePrepStmts", "true");
        hikariConfig.addDataSourceProperty("prepStmtCacheSize", "250");
        hikariConfig.addDataSourceProperty("prepStmtCacheSqlLimit", "2048");

        HikariDataSource ds = new HikariDataSource(hikariConfig);
        Connection conn;
        Statement statement;
        ResultSet rs;

        try {

            // 创建connection
            conn = ds.getConnection();
            statement = conn.createStatement();
            String sql = "select * from t_blog limit ?";
            PreparedStatement statement1 = conn.prepareStatement(sql);
            statement1.setInt(1, 2);
            rs = statement1.executeQuery();

            // 执行sql
            // rs = statement.executeQuery("select * from t_blog");


            // 取数据
            while (rs.next()) {
                System.out.println(rs.getString("title"));
            }

            //
            rs.close();

            statement.close();

            // 关闭connection
            conn.close();
        } catch (SQLException e) {
            e.printStackTrace();
        }

    }

}

```