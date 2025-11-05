Properties 继承于 Hashtable，用于管理配置信息的类。-->它和HashMap类很相似，但是它支持同步。

由于 Properties 继承自 Hashtable 类，因此具有 Hashtable 的所有功能，同时还提供了一些特殊的方法来读取和写入属性文件。

Properties 类常用于存储程序的配置信息，例如数据库连接信息、日志输出配置、应用程序设置等。使用Properties类，可以将这些信息存储在一个文本文件中，并在程序中读取这些信息。

Properties 类被许多 Java 类使用。例如，在获取环境变量时它就作为 System.getProperties() 方法的返回值。

Properties 定义如下实例变量。这个变量持有一个 Properties 对象相关的==默认属性列表==。

```
Properties defaults;
```

**构造方法**



```java
//第一种
Properties prop = new Properties();

//使用propDefault 作为默认值。两种情况下，属性列表都为空
Properties prop = new Properties(Properties propDefault);
```



除了从 Hashtable 中所定义的方法，Properties 还定义了以下方法：

|                         **序号**                         | **方法描述**                                                 |
| :------------------------------------------------------: | :----------------------------------------------------------- |
|             `String getProperty(String key)`             | 用指定的键在此属性列表中搜索属性。                           |
| `String getProperty(String key, String defaultProperty)` | 用指定的键在属性列表中搜索属性。                             |
|            `void list(PrintStream streamOut)`            | 将属性列表输出到指定的输出流。                               |
|            `void list(PrintWriter streamOut)`            | 将属性列表输出到指定的输出流。                               |
|   `void load(InputStream streamIn) throws IOException`   | 从输入流中读取属性列表（键和元素对）。                       |
|              `Enumeration propertyNames( )`              | 按简单的面向行的格式从输入字符流中读取属性列表（键和元素对）。 |
|      `Object setProperty(String key, String value)`      | 调用 Hashtable 的方法 put。                                  |
| `void store(OutputStream streamOut, String description)` | 以适合使用 load(InputStream)方法加载到 Properties 表中的格式，将此 Properties 表中的属性列表（键和元素对）写入输出流。 |

Properties 类提供了多种读取和写入属性文件的方法。其中最常用的方法是 load() 和 store() 方法。

load() 方法可以从文件中读取属性，而 store() 方法可以将属性写入文件。

下面是一个简单的例子，演示了如何使用 Properties 类来读取和写入属性文件：

## 实例

```java
import java.io.*;
import java.util.Properties;

public class PropertiesExample {
    public static void main(String[] args) {
        Properties prop = new Properties();

        try {
            // 读取属性文件
            prop.load(new FileInputStream("config.properties"));

            // 获取属性值
            String username = prop.getProperty("username");
            String password = prop.getProperty("password");

            // 输出属性值
            System.out.println("username: " + username);
            System.out.println("password: " + password);

            // 修改属性值
            prop.setProperty("username", "newUsername");
            prop.setProperty("password", "newPassword");

            // 保存属性到文件
            prop.store(new FileOutputStream("config.properties"), null);

        } catch (IOException ex) {
            ex.printStackTrace();
        }
    }
}
```





以上实例中我们创建了一个 Properties 对象，然后使用 load() 方法从配置文件中读取属性。接着，我们使用 getProperty() 方法获取属性值，并输出到控制台。然后，我们使用 setProperty() 方法修改属性值，并使用 store() 方法将修改后的属性保存回文件。