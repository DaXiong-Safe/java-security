相关漏洞
---
- pre-auth  SSRF/FileRead - custom.jsp
- post-auth SQLi - kmImeetingRes.do
- post-auth XMLDecoderDeserialization - sysSearchMain.do
- post-auth RCE = getBean() + bsh.Interpreter - dataxml.jsp
- post-auth JDBC RCE - admin.do

利用研究
---

### 配置文件解密 - admin.properties

文件位置
> ekp/WEB-INF/KmssConfig/admin.properties

解密工具
- https://github.com/zhutougg/LandrayDES



### 配置文件解密 - kmssconfig.properties
文件位置

> ekp/WEB-INF/KmssConfig/kmssconfig.properties

example

![image](https://user-images.githubusercontent.com/55024146/178807547-9882a2d1-7c1d-487e-af42-28a610a8fcaf.png)


解密代码实现

```java
package org.example;

import java.io.*;
import java.nio.file.Files;
import java.nio.file.Paths;
import com.landray.kmss.sys.config.action.SysConfigAdminUtil;

public class SysConfigDecrypt {
    public static void main(String[] args) throws Exception {
        InputStream in = Files.newInputStream(Paths.get("H:\\landray\\ekp\\WEB-INF\\KmssConfig\\kmssconfig.properties"));
        InputStreamReader inr = new InputStreamReader(SysConfigAdminUtil.doPropertiesDecrypt(in));
        BufferedReader br = new BufferedReader(inr);
        String line;
        StringBuilder sb = new StringBuilder();
        while((line = br.readLine()) != null){
            sb.append(line).append("\r\n");
        }
        System.out.println(sb);
    }
}
```


解密效果如图

![image](https://user-images.githubusercontent.com/55024146/178808195-4c7c822d-36bb-47ac-a54e-8a0ce7014581.png)

