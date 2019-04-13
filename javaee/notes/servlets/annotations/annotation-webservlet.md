---
description: Все про аннотацию WebServlet
---

# @WebServlet

Оригинал статьи - [тут](https://www.codejava.net/java-ee/servlet/webservlet-annotation-examples).

Аннотация `@WebServlet`появилась в Servlet Api 3.0 \(Java EE6\)  в 2010 году. Она используется для объявления сервлета.

 Аннотируемый класс должен быть наследником`javax.servlet.http.HttpServlet`.

**Синтаксис**

```java
@WebServlet( attribute1=value1, 
             attribute2=value2,
                ...
            )
public class TheServlet extends javax.servlet.http.HttpServlet {
    // servlet code...
}
```

**Аттрибуты**

<table>
  <thead>
    <tr>
      <th style="text-align:left">&#x418;&#x43C;&#x44F;</th>
      <th style="text-align:left"><b>&#x422;&#x438;&#x43F;</b>
      </th>
      <th style="text-align:left">&#x41E;&#x431;&#x44F;&#x437;&#x430;&#x442;&#x435;&#x43B;&#x44C;&#x43D;&#x43E;&#x441;&#x442;&#x44C;</th>
      <th
      style="text-align:left">&#x41E;&#x43F;&#x438;&#x441;&#x430;&#x43D;&#x438;&#x435;</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td style="text-align:left">
        <p><b>value</b>
        </p>
        <p>or</p>
        <p><b>urlPatterns</b>
        </p>
      </td>
      <td style="text-align:left">String[]</td>
      <td style="text-align:left">Required</td>
      <td style="text-align:left">&#x423;&#x43A;&#x430;&#x437;&#x44B;&#x432;&#x430;&#x435;&#x442; &#x43E;&#x434;&#x438;&#x43D;
        &#x438;&#x43B;&#x438; &#x431;&#x43E;&#x43B;&#x44C;&#x448;&#x435; URL &#x43F;&#x430;&#x442;&#x442;&#x435;&#x440;&#x43D;&#x43E;&#x432;
        &#x441;&#x435;&#x440;&#x432;&#x43B;&#x435;&#x442;&#x430;. &#x422;&#x43E;&#x43B;&#x44C;&#x43A;&#x43E;
        &#x43E;&#x434;&#x43D;&#x43E; &#x438;&#x437; &#x437;&#x43D;&#x430;&#x447;&#x435;&#x43D;&#x438;&#x439;
        &#x43C;&#x43E;&#x436;&#x435;&#x442; &#x431;&#x44B;&#x442;&#x44C; &#x438;&#x441;&#x43F;&#x43E;&#x43B;&#x44C;&#x437;&#x43E;&#x432;&#x430;&#x43D;&#x43E;</td>
    </tr>
    <tr>
      <td style="text-align:left"><b>name</b>
      </td>
      <td style="text-align:left">String</td>
      <td style="text-align:left">Optional</td>
      <td style="text-align:left">&#x418;&#x43C;&#x44F; &#x441;&#x435;&#x440;&#x432;&#x43B;&#x435;&#x442;&#x430;</td>
    </tr>
    <tr>
      <td style="text-align:left"><b>displayName</b>
      </td>
      <td style="text-align:left">String</td>
      <td style="text-align:left">Optional</td>
      <td style="text-align:left">&#x41E;&#x442;&#x43E;&#x431;&#x440;&#x430;&#x436;&#x430;&#x435;&#x43C;&#x43E;&#x435;(<em>display</em>)
        &#x438;&#x43C;&#x44F; &#x441;&#x435;&#x440;&#x432;&#x43B;&#x435;&#x442;&#x430;</td>
    </tr>
    <tr>
      <td style="text-align:left"><b>description</b>
      </td>
      <td style="text-align:left">String</td>
      <td style="text-align:left">Optional</td>
      <td style="text-align:left">&#x41E;&#x43F;&#x438;&#x441;&#x430;&#x43D;&#x438;&#x435; &#x441;&#x435;&#x440;&#x432;&#x43B;&#x435;&#x442;&#x430;</td>
    </tr>
    <tr>
      <td style="text-align:left"><b>asyncSupported</b>
      </td>
      <td style="text-align:left">boolean</td>
      <td style="text-align:left">Optional</td>
      <td style="text-align:left">&#x423;&#x43A;&#x430;&#x437;&#x44B;&#x432;&#x430;&#x435;&#x442; &#x43F;&#x43E;&#x434;&#x434;&#x435;&#x440;&#x436;&#x438;&#x432;&#x430;&#x435;&#x442;
        &#x43B;&#x438; &#x441;&#x435;&#x440;&#x432;&#x43B;&#x435;&#x442; &#x430;&#x441;&#x438;&#x43D;&#x445;&#x440;&#x43E;&#x43D;&#x43D;&#x44B;&#x439;
        &#x440;&#x430;&#x431;&#x43E;&#x447;&#x438;&#x439; &#x440;&#x435;&#x436;&#x438;&#x43C;.
        False &#x43F;&#x43E; &#x443;&#x43C;&#x43B;&#x43E;&#x447;&#x430;&#x43D;&#x438;&#x44E;</td>
    </tr>
    <tr>
      <td style="text-align:left"><b>initParams</b>
      </td>
      <td style="text-align:left">WebInitParam[]</td>
      <td style="text-align:left">Optional</td>
      <td style="text-align:left">&#x423;&#x43A;&#x430;&#x437;&#x44B;&#x432;&#x430;&#x435;&#x442; &#x43D;&#x430;
        &#x43E;&#x434;&#x438;&#x43D; &#x438;&#x43B;&#x438; &#x431;&#x43E;&#x43B;&#x44C;&#x448;&#x435;
        &#x43F;&#x430;&#x440;&#x430;&#x43C;&#x435;&#x442;&#x440;&#x43E;&#x432;
        &#x438;&#x43D;&#x438;&#x446;&#x438;&#x430;&#x43B;&#x438;&#x437;&#x430;&#x446;&#x438;&#x438;
        &#x441;&#x435;&#x440;&#x432;&#x43B;&#x435;&#x442;&#x430;. &#x41A;&#x430;&#x436;&#x434;&#x44B;&#x439;
        &#x43F;&#x430;&#x440;&#x430;&#x43C;&#x435;&#x442;&#x440; &#x443;&#x43A;&#x430;&#x437;&#x44B;&#x432;&#x430;&#x435;&#x442;&#x441;&#x44F;
        &#x441; &#x43F;&#x43E;&#x43C;&#x43E;&#x449;&#x44C;&#x44E; &#x430;&#x43D;&#x43D;&#x43E;&#x442;&#x430;&#x446;&#x438;&#x438;
        <a
        href="https://www.codejava.net/java-ee/servlet/webinitparam-annotation-examples">@WebInitParam</a>
      </td>
    </tr>
    <tr>
      <td style="text-align:left"><b>loadOnStartup</b>
      </td>
      <td style="text-align:left">int</td>
      <td style="text-align:left">Optional</td>
      <td style="text-align:left">&#x423;&#x43A;&#x430;&#x437;&#x44B;&#x432;&#x430;&#x435;&#x442; &#x43F;&#x43E;&#x440;&#x44F;&#x434;&#x43E;&#x43A;
        &#x437;&#x430;&#x433;&#x440;&#x443;&#x437;&#x43A;&#x438; &#x43F;&#x440;&#x438;
        &#x437;&#x430;&#x43F;&#x443;&#x441;&#x43A;&#x435;(<em>load-on-startup</em>)
        &#x441;&#x435;&#x440;&#x432;&#x43B;&#x435;&#x442;&#x430;.</td>
    </tr>
    <tr>
      <td style="text-align:left"><b>smallIcon</b>
      </td>
      <td style="text-align:left">String</td>
      <td style="text-align:left">Optional</td>
      <td style="text-align:left">&#x423;&#x43A;&#x430;&#x437;&#x44B;&#x432;&#x430;&#x435;&#x442; &#x438;&#x43C;&#x44F;
        &#x43C;&#x430;&#x43B;&#x435;&#x43D;&#x44C;&#x43A;&#x43E;&#x439; &#x438;&#x43A;&#x43E;&#x43D;&#x43A;&#x438;
        &#x441;&#x435;&#x440;&#x432;&#x43B;&#x435;&#x442;&#x430;</td>
    </tr>
    <tr>
      <td style="text-align:left"><b>largeIcon</b>
      </td>
      <td style="text-align:left">String</td>
      <td style="text-align:left">Optional</td>
      <td style="text-align:left">&#x423;&#x43A;&#x430;&#x437;&#x44B;&#x432;&#x430;&#x435;&#x442; &#x438;&#x43C;&#x44F;
        &#x431;&#x43E;&#x43B;&#x44C;&#x448;&#x43E;&#x439; &#x438;&#x43A;&#x43E;&#x43D;&#x43A;&#x438;
        &#x441;&#x435;&#x440;&#x432;&#x43B;&#x435;&#x442;&#x430;</td>
    </tr>
  </tbody>
</table>**NOTE:** атрибуты displayName, description, small Icon и largeIcon в основном используются инструментами, IDE или контейнерами сервлетов, они не влияют на работу сервлета.

## **Примеры**

* **Сервлет аннотированный только с одним URL паттерном:**

```java
import java.io.IOException;
 
import javax.servlet.annotation.WebServlet;
import javax.servlet.http.HttpServlet;
import javax.servlet.http.HttpServletRequest;
import javax.servlet.http.HttpServletResponse;
 
@WebServlet("/processForm")
public class MyServlet extends HttpServlet {
    public void doGet(HttpServletRequest request, HttpServletResponse response)
            throws IOException {
        response.getWriter().println("Hello");
    }
}
```

Сервлет  `MyServlet`  сопоставляется URL паттерну `/processForm`. При доступе к этому сервлету, он вернет _“Hello”_.

* **Сервлет аннотированный несколькими URL паттернами:**

```java
import javax.servlet.annotation.WebServlet;
import javax.servlet.http.HttpServlet;
 
@WebServlet(urlPatterns = {"/sendFile", "/uploadFile"})
public class UploadServlet extends HttpServlet {
    // implement servlet doPost() and doGet()...
}
```

Здесь сервлет `UploadServlet` можно получить через два шаблона URL:  `/sendFile` и  `/upload File`.

* **Сервлет с дополнительной информацией**

```java
import javax.servlet.annotation.WebServlet;
import javax.servlet.http.HttpServlet;
 
@WebServlet(
        name = "MyOwnServlet",
        description = "This is my first annotated servlet",
        urlPatterns = "/processServlet"
)
public class MyServlet extends HttpServlet {
    // implement servlet doPost() and doGet()...
}
```

* **Сервлет с несколькими параметрами инициализации**

```java
import java.io.IOException;
import java.io.PrintWriter;
 
import javax.servlet.annotation.WebInitParam;
import javax.servlet.annotation.WebServlet;
import javax.servlet.http.HttpServlet;
import javax.servlet.http.HttpServletRequest;
import javax.servlet.http.HttpServletResponse;
 
@WebServlet(
        urlPatterns = "/imageUpload",
        initParams =
        {
            @WebInitParam(name = "saveDir", value = "D:/FileUpload"),
            @WebInitParam(name = "allowedTypes", value = "jpg,jpeg,gif,png")
        }
)
public class ImageUploadServlet extends HttpServlet {
 
    public void doGet(HttpServletRequest request, HttpServletResponse response)
            throws IOException {
        String saveDir = getInitParameter("saveDir");
        String fileTypes = getInitParameter("allowedTypes");
 
        PrintWriter writer = response.getWriter();
 
        writer.println("saveDir = " + saveDir);
        writer.println("fileTypes = " + fileTypes);
    }
}
```

Здесь мы объявляем сервлет `ImageUploadServlet`, сопоставленный шаблону URL `/imageUpload`, и указываем два параметра `saveDir` и `allowedTypes`. Метод `doGet ()` извлекает значения этих параметров и распечатывает их клиенту.

* **Объявление сервлета с асинхронным режимом работы и порядком загрузки при запуске:**

```java
import javax.servlet.ServletConfig;
import javax.servlet.annotation.WebServlet;
import javax.servlet.http.HttpServlet;
 
@WebServlet(
        urlPatterns = "/myController",
        loadOnStartup = 1,
        asyncSupported = true
)
public class StartupServlet extends HttpServlet {
     
    public void init(ServletConfig config) {
        System.out.println("My servlet has been initialized");
    }
     
    // implement servlet doPost() and doGet()...
}
```

Здесь мы объявляем сервлет `StartupServlet` с `loadOnStartup` = 1, Что означает, что этот сервлет инициализируется автоматически контейнером сервлета при запуске сервера \(будет напечатано сообщение в методе `init ()`\). Мы также указываем, что сервлет поддерживает асинхронный режим.

