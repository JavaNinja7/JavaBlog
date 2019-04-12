---
description: Java EE API
---

# Java EE APIs

![Java EE8 API](../../../../.gitbook/assets/javaee8.png)

В следующих разделах приводится краткая сводка технологий, требуемых платформой Java EE и API, используемыми в приложениях Java EE.

#### Enterprise JavaBeans Technology <a id="_enterprise_javabeans_technology"></a>

Компонент Enterprise JavaBeans \(EJB\) или компонент enterprise bean-это тело кода, которое имеет поля и методы для реализации модулей бизнес-логики. Корпоративный компонент можно рассматривать как строительный блок, который можно использовать отдельно или с другими корпоративными компонентами для выполнения бизнес-логики на сервере Java EE.

Корпоративные компоненты-это либо сеансовые\(session\) компоненты, либо компоненты, управляемые сообщениями\(message-driven\).

* Сеансовый компонент представляет собой временное общение с клиентом. Когда код клиента завершает исполнение, сеансовый компонент и его данные исчезают.
* Управляемый сообщениями компонент объединяет функции сеансового компонента и прослушивателя сообщений, позволяя бизнес-компоненту асинхронно получать сообщения. Обычно это сообщения службы сообщений Java \(JMS\).

Платформа Java EE 8 требует Enterprise JavaBeans 3.2 и Interceptors 1.2. Спецификация Interceptors является частью спецификации EJB.

#### Java Servlet Technology <a id="_java_servlet_technology"></a>

Технология Java сервлетов позволяет определить  HTTP-специфичные сервлет классы. Класс сервлетов расширяет возможности серверов, на которых размещаются приложения, доступные с помощью модели программирования запрос-ответ. Хотя сервлеты могут отвечать на запросы любого типа, они обычно используются для расширения приложений, размещенных на веб-серверах.

В платформе Java EE 8 новые возможности технологии сервлетов включают следующее:

* [Server Push](https://habr.com/ru/company/badoo/blog/329722/)
* [HTTP Trailer](http://hantsy.blogspot.com/2017/11/servlet-40-http-trailer.html)

Java EE 8 платформа требует версиию Servlet 4.0

#### JavaServer Faces Technology <a id="_javaserver_faces_technology"></a>

JavaServer Faces Technology - это платформа пользовательского интерфейса для создания веб-приложений. Основными компонентами технологии Javaserver Faces являются следующие:

* Фремйворк GUI компонентов.
* Гибкая модель для рендеринга компонентов в различных видах HTML или различных языках разметки и технологиях. Объект`Renderer`создает разметку для отображения компонента и преобразует данные, хранящиеся в объекте модели, в типы, которые могут быть отображены в представлении.
* Стандартный `RenderKit` для генерации разметки HTML 4.01. \(Вроде как старая версия, может ошибка здесь\)

Компоненты GUI поддерживают следующие функции:

* Валидация ввода
* Обработка событий
* Преобразование данных между объектами и компонентами модели
* Создание объекта управляемой модели
* Настройка навигации по страницам
* Expression Language \(EL\)

Все эти функции доступны с помощью стандартных API Java и XML-файлов конфигурации.

В платформе Java EE 8 Новые возможности технологии Javaserver Faces включают следующее:

* Прямая поддержка  WebSockets через новый тег `<f:websocket>`
* Class-level bean валидация через новый тег `<f:validateWholeBean>`
* CDI-совместимый `@ManagedProperty` аннотация
* Enhanced component search expression framework

Платформа Java EE 8  требует версии JavaServer Faces 2.3 and Expression Language 3.0.

Для отличной сводки того что нового в  JSF 2.3,  смотреть [тут](https://javaserverfaces.github.io/users.html) .

#### JavaServer Pages Technology <a id="_javaserver_pages_technology"></a>

JavaServer Pages \(JSP\) технология позволяет вставлять сниппеты кода сервлетов прямо в тексто-ориентрованный документ. JSP страница это текстовый документ, который содержит два вида текста:

* Статические данные, которые могут быть выражены в любом текстовом формате, таком как HTML или XML
* Элементы JSP, которые определяют, как страница конструирует динамическое содержимое

Для информации о JSP технологии,  смотри [_The Java EE 5 Tutorial_](http://docs.oracle.com/javaee/5/tutorial/doc/) .

Платформа Java EE 8 требует Java Server Pages 2.3 для совместимости с более ранними выпусками, но рекомендует использовать Facelets в качестве технологии отображения в новых приложениях.

#### JavaServer Pages Standard Tag Library <a id="_javaserver_pages_standard_tag_library"></a>

Стандартная библиотека тегов JavaServer Pages \(JSTL\) инкапсулирует основные функции, общие для многих приложений JSP. Вместо смешивания тегов от многочисленных поставщиков в приложениях JSP используется один стандартный набор тегов. Эта стандартизация позволяет развертывать приложения на любом контейнере JSP, поддерживающем JSTL, и повышает вероятность оптимизации реализации тегов.

JSTL имеет итератор и условные теги для обработки управления потоком, теги для управления XML-документами, теги интернационализации, теги для доступа к базам данных с использованием SQL и теги для часто используемых функций.

Платформа Java EE 8 требует JSTL 1.2.

#### Java Persistence API <a id="_java_persistence_api"></a>

Java Persistence API \(JPA\)–это решение на основе стандартов Java для персистентности. Персистентность использует подход объектно-реляционного сопоставления для преодоления разрыва между объектно-ориентированной моделью и реляционной базой данных. JPA также может использоваться в приложениях Java SE вне среды Java EE. Persistence состоит из следующих областей:

* The Java Persistence API
* язык запросов
* Метаданные объектно-реляционного маппинга\(_mapping_\)

Для Java EE 8 требуется Java Persistence API 2.2.

#### Java Transaction API <a id="_java_transaction_api"></a>

API транзакций Java \(JTA\) предоставляет стандартный интерфейс для демаркации транзакций. Архитектура Java EE предоставляет автокоммиты по умолчанию для обработки тразакционных коммитов и отката транзакций. Автокоммит означает, что любые другие приложения, просматривающие данные, будут видеть обновленные данные после каждой операции чтения или записи базы данных. Однако если приложение выполняет две отдельные операции доступа к базе данных, которые зависят друг от друга, необходимо использовать API JTA для разграничения, где начинается, откатывается и фиксируется\(_commits_\) вся транзакция, включая обе операции.

Для Java EE 8 требуется Java Transaction API 1.2.

#### Java API for RESTful Web Services <a id="_java_api_for_restful_web_services"></a>

API Java для веб-служб RESTful \(JAX-RS\) определяет API для разработки веб-служб, построенных в соответствии с архитектурным стилем передачи состояния представления \(REST - Representational State Transfer\). Приложение JAX-RS-это веб-приложение, которое состоит из классов, упакованных в виде сервлета в файл WAR вместе с необходимыми библиотеками.

В платформе Java EE 8,  следующие новые особенности RESTful web-сервисов:

* Reactive Client API

  When the results of an invocation on a target resource are received, enhancements to the completion stage APIs in Java SE allow the sequence of those results to be specified, prioritized, combined, or concatenated, and how exceptions can be handled.

* Улучшение  в поддержке  server-sent событий

  Клиенты могут подписаться на уведомления о событиях, выданные сервером, используя длительное соединение. Добавлена поддержка нового типа media-text / event-stream.

* Поддержка [JSON-B](https://toster.ru/q/315910) обьектов, и улучшенная интеграция с технологиями CDI, Servlet, and Bean Validation 

Платформа Java EE 8  требует  JAX-RS 2.1.

#### Managed Beans <a id="_managed_beans"></a>

Managed Beans, lightweight container-managed objects \(POJOs\) with minimal requirements, support a small set of basic services, such as resource injection, lifecycle callbacks, and interceptors. Managed Beans represent a generalization of the managed beans specified by JavaServer Faces technology and can be used anywhere in a Java EE application, not just in web modules.

The Managed Beans specification is part of the Java EE 8 platform specification \(JSR 366\). The Java EE 8 platform requires Managed Beans 1.0.

#### Contexts and Dependency Injection for Java EE <a id="_contexts_and_dependency_injection_for_java_ee"></a>

Contexts and Dependency Injection for Java EE \(CDI\) defines a set of contextual services, provided by Java EE containers, that make it easy for developers to use enterprise beans along with JavaServer Faces technology in web applications. Designed for use with stateful objects, CDI also has many broader uses, allowing developers a great deal of flexibility to integrate different kinds of components in a loosely coupled but typesafe way.

In the Java EE 8 platform, new CDI features include the following:

* An API for bootstrapping a CDI container in Java SE 8
* Support for observer ordering, which determines the order in which the observer methods for a particular event are invoked, and support for firing events asynchronously
* Configurators interfaces, which are used for dynamically defining and modifying CDI objects
* Built-in annotation literals, a convenience feature for creating instances of annotations, and more

The Java EE 8 platform requires CDI 2.0.

#### Dependency Injection for Java <a id="_dependency_injection_for_java"></a>

Dependency Injection for Java defines a standard set of annotations \(and one interface\) for use on injectable classes.

In the Java EE platform, CDI provides support for Dependency Injection. Specifically, you can use injection points only in a CDI-enabled application.

The Java EE 8 platform requires Dependency Injection for Java 1.0.

#### Bean Validation <a id="_bean_validation"></a>

The Bean Validation specification defines a metadata model and API for validating data in JavaBeans components. Instead of distributing validation of data over several layers, such as the browser and the server side, you can define the validation constraints in one place and share them across the different layers.

In the Java EE 8 platform, new Bean Validation features include the following:

* Support for new features in Java SE 8, such as the Date-Time API
* Addition of new built-in Bean Validation constraints

The Java EE 8 platform requires Bean Validation 2.0.

#### Java Message Service API <a id="_java_message_service_api"></a>

The Java Message Service \(JMS\) API is a messaging standard that allows Java EE application components to create, send, receive, and read messages. It enables distributed communication that is loosely coupled, reliable, and asynchronous.

The Java EE 8 platform requires JMS 2.0.

#### Java EE Connector Architecture <a id="_java_ee_connector_architecture"></a>

The Java EE Connector Architecture is used by tools vendors and system integrators to create resource adapters that support access to enterprise information systems that can be plugged in to any Java EE product. A resource adapter is a software component that allows Java EE application components to access and interact with the underlying resource manager of the EIS. Because a resource adapter is specific to its resource manager, a different resource adapter typically exists for each type of database or enterprise information system.

The Java EE Connector Architecture also provides a performance-oriented, secure, scalable, and message-based transactional integration of Java EE platform–based web services with existing EISs that can be either synchronous or asynchronous. Existing applications and EISs integrated through the Java EE Connector Architecture into the Java EE platform can be exposed as XML-based web services by using JAX-WS and Java EE component models. Thus JAX-WS and the Java EE Connector Architecture are complementary technologies for enterprise application integration \(EAI\) and end-to-end business integration.

The Java EE 8 platform requires Java EE Connector Architecture 1.7.

#### JavaMail API <a id="_javamail_api"></a>

Java EE applications use the JavaMail API to send email notifications. The JavaMail API has two parts:

* An application-level interface used by the application components to send mail
* A service provider interface

The Java EE platform includes the JavaMail API with a service provider that allows application components to send Internet mail.

The Java EE 8 platform requires JavaMail 1.6.

#### Java Authorization Contract for Containers <a id="_java_authorization_contract_for_containers"></a>

The Java Authorization Contract for Containers \(JACC\) specification defines a contract between a Java EE application server and an authorization policy provider. All Java EE containers support this contract.

The JACC specification defines `java.security.Permission` classes that satisfy the Java EE authorization model. The specification defines the binding of container-access decisions to operations on instances of these permission classes. It defines the semantics of policy providers that use the new permission classes to address the authorization requirements of the Java EE platform, including the definition and use of roles.

The Java EE 8 platform requires JACC 1.5.

#### Java Authentication Service Provider Interface for Containers <a id="_java_authentication_service_provider_interface_for_containers"></a>

The Java Authentication Service Provider Interface for Containers \(JASPIC\) specification defines a service provider interface \(SPI\) by which authentication providers that implement message authentication mechanisms may be integrated in client or server message-processing containers or runtimes. Authentication providers integrated through this interface operate on network messages provided to them by their calling containers. The authentication providers transform outgoing messages so that the source of each message can be authenticated by the receiving container, and the recipient of the message can be authenticated by the message sender. Authentication providers authenticate each incoming message and return to their calling containers the identity established as a result of the message authentication.

The Java EE 8 platform requires JASPIC 1.1.

#### Java EE Security API <a id="java-ee-security-api"></a>

The Java EE Security API specification defines portable, plug-in interfaces for HTTP authentication and identity stores, and an injectable SecurityContext interface that provides an API for programmatic security.

Implementations of the `HttpAuthenticationMechanism` interface can be used to authenticate callers of web applications. An application can supply its own `HttpAuthenticationMechanism`, or use one of the default implementations provided by the container.

Implementations of the `IdentityStore` interface can be used to validate user credentials and retrieve group information. An application can provide its own `IdentityStore`, or use the built in LDAP or Database store.

The `HttpAuthenticationMechanism` and `IdentityStore` APIs provide an advantage over container-provided implementations in that they allow an application to control the authentication process, and the identity stores used for authentication, in a standard, portable way.

The `SecurityContext` API is intended for use by application code to query and interact with the current security context. The specification also provides for default group-to-role mapping, and defines a principal type called `CallerPrincipal` that can represent the identity of an application caller.

The Java EE 8 platform requires Java EE Security API 1.0.

#### Java API for WebSocket <a id="_java_api_for_websocket"></a>

WebSocket is an application protocol that provides full-duplex communications between two peers over TCP. The Java API for WebSocket enables Java EE applications to create endpoints using annotations that specify the configuration parameters of the endpoint and designate its lifecycle callback methods.

The Java EE 8 platform requires Java API for WebSocket 1.1.

#### Java API for JSON Processing <a id="_java_api_for_json_processing"></a>

JavaScript Object Notation \(JSON\) is a text-based data exchange format derived from JavaScript that is used in web services and other connected applications. The Java API for JSON Processing \(JSON-P\) enables Java EE applications to parse, transform, and query JSON data using the object model or the streaming model.

In the Java EE 8 platform, new features of JSON-P include support for the following:

* JSON Pointer

  Defines a string syntax for referencing a specific value within a JSON document. JSON Pointer includes APIs for extracting values from a target document and transforming them to create a new JSON document.

* JSON Patch

  Defines a format for expressing a sequence of operations to be applied to a JSON document.

* JSON Merge Patch

  Defines a format and processing rules for applying operations to a JSON document that are based upon specific content of the target document.

* The addition of editing and transformation functions to basic JSON document processing.
* Helper classes and methods, called JSON Collectors, which leverage features of the Stream API that was introduced in Java SE 8.

The Java EE 8 platform requires JSON-P 1.1.

#### Java API for JSON Binding <a id="java-api-for-json-binding"></a>

The Java API for JSON Binding \(JSON-B\) provides a binding layer for converting Java objects to and from JSON messages. JSON-B also supports the ability to customize the default mapping process used in this binding layer through the use of Java annotations for a given field, JavaBean property, type or package, or by providing an implementation of a property naming strategy.

JSON-B is new to the Java EE 8 platform. The Java EE 8 platform requires JSON-B 1.0.

#### Concurrency Utilities for Java EE <a id="_concurrency_utilities_for_java_ee"></a>

Concurrency Utilities for Java EE is a standard API for providing asynchronous capabilities to Java EE application components through the following types of objects: managed executor service, managed scheduled executor service, managed thread factory, and context service.

The Java EE 8 platform requires Concurrency Utilities for Java EE 1.0.

#### Batch Applications for the Java Platform <a id="_batch_applications_for_the_java_platform"></a>

Batch jobs are tasks that can be executed without user interaction. The Batch Applications for the Java Platform specification is a batch framework that provides support for creating and running batch jobs in Java applications. The batch framework consists of a batch runtime, a job specification language based on XML, a Java API to interact with the batch runtime, and a Java API to implement batch artifacts.

The Java EE 8 platform requires Batch Applications for the Java Platform 1.0.

