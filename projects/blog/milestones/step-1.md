---
description: Первый шаг.
---

# Step 1

Оригинальный туториал [здесь](https://metanit.com/java/javaee/). Буду дергать оттуда полезную инфу. 

Создал обычный пустой maven проект. Затем в пустой папке создал директорию `web` с `index.html` и поддиректорию `WEB-INF` с файлом `web.xml`. 

Немного о `web.xml.`

Далее буду следовать туториалу от метанита, но постараюсь все делать ручками без волшебных плагинов к средам разработки. 

Как оказалось web.xml не нужен в простых случаях, так как появилась аннотация `@WebServlet`. Надо сделать про нее отдельную ссылку.   


Создал простейший сервлет:

```java
import javax.servlet.*;

@WebServlet("/hello")
public class HelloServlet extends HttpServlet {

	protected void doGet(HttpServletRequest request, HttpServletResponse response) {

	/*
	....
	*/
	}
}
```

Скомпилировал HelloServlet командой : 

```bash
javac -cp "/opt/tomcat9/lib/servlet-api.jar" HelloServlet.java
```

Подробнее о classpath тут. Файл servlet-api.jar содержит реализацию java ee спецификаций сервлетов.   

Создал следующую иерархию папок в CATALINA\_HOME \(_Catalina - Старое название Tomcat_\)

```text
helloapp
└── WEB-INF
    └── classes
        ├── HelloServlet.class
        └── HelloServlet.java
```

