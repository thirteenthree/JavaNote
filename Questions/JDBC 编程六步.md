

```Java
import java.sql.Driver;
import java.sql.DriverManager;
import java.sql.SQLException;
import java.sql.Connection;
import java.sql.Statement;
public class JDBCConnect{
    public static void main(String[] args){
        Connection conn=null;
        Statement stmt = null;
        try{
            //1.注册驱动
            Driver driver = new com.mysql.jdbc.Driver();
            DriverManager.registerDriver(driver);
            // 2. 获取连接
            String url = "jdbc:mysql://127.0.0.1:3306/dabasename";
            String user = "root";
            String password = "123";
            conn = DriverManager.getConnection(url,user,password);
            System.out.println("数据库连接对象 = " + conn);
            //3. 获取数据库操作对象
            stmt = conn.createStatement();
            
            // 4. 执行sql
            String sql = " ";
            //专门执行DML语句(insert delete update)
            //返回值是"影响数据库中的记录条数";
            int count = stmt.executeUpdate(sql);
            //5. 处理查询结果集
        }catch(SQLException e){
            e.printStackTrace();
        }finally{
            //6. 释放资源
            //要遵循从小到大一次关闭
            try{
                if (stmt!=null){
                stmt.close();
            }
            }catch(SQLException e){
            	e.printStackTrace();
            }
            try{
                if (conn!=null){
                conn.close();
                }
            }
            }catch(SQLException e){
            	e.printStackTrace();
            }
           
        }
    }
}
```



