相关漏洞
---

### JNDI Injection 

- https://mp.weixin.qq.com/s/nusGsstudrQt2dwZxHXKgg



利用研究
---

### 数据库密码解密

数据库配置文件位置

> /ierp/bin/prop.xml

example

```
<dataSource>
<dataSourceName>nc</dataSourceName>
<oidMark>C2</oidMark>
<databaseUrl>jdbc:sqlserver://127.0.0.1:1433;database=nc;sendStringParametersAsUnicode=false</databaseUrl>
<user>nc</user>
<password>jlehfdffcfmohiag</password>
<driverClassName>com.microsoft.sqlserver.jdbc.SQLServerDriver</driverClassName>
<databaseType>SQLSERVER</databaseType>
<maxCon>50</maxCon>
<minCon>10</minCon>
<dataSourceClassName>nc.bs.mw.ejb.xares.IerpDataSource</dataSourceClassName>
<xaDataSourceClassName>nc.bs.mw.ejb.xares.IerpXADataSource</xaDataSourceClassName>
<conIncrement>0</conIncrement>
<conInUse>0</conInUse>
<conIdle>0</conIdle>
</dataSource>
```

效果如图：

![image](https://user-images.githubusercontent.com/55024146/178786818-366dc752-2f40-4b80-9dbf-98e206aa732c.png)



