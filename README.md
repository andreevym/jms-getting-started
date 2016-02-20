Title: jms-getting-started
Description:
This section describes the sending and receiving message. Getting started with the GlassFish application server.


1) Установил glassfish.
https://glassfish.java.net/download.html

2) Распаковал и запустил
asadmin start-domain

3) Из-за баги в UI glassfish добавилял ресурсы (фабрику соединений и очередь) через консоль:

3.1) Зашел в панель управление через cmd
asadmin

3.2) Добавил фабрику.
asadmin> create-jms-resource --host localhost --port 4848 --restype javax.jms.QueueConnectionFactory --property  Name=MyQCF jms/QCF1

![JMS-Connection-Factory](http://i2.wp.com/blog.jelastic.com/wp-content/uploads/2013/08/JMS-Connection-Factory.gif)

3.3) Добавил очередь.
create-jms-resource --host localhost --port 4848 --restype javax.jms.Queue --property Name=PhysicalQueue jms/myQueue

![JMS-Destination-Resource](http://i2.wp.com/blog.jelastic.com/wp-content/uploads/2013/08/JMS-Destination-Resource.gif)

4) Доработал проект:
изменил зависимость, на:
<dependency>
    <groupId>javax.jms</groupId>
    <artifactId>javax.jms-api</artifactId>
    <version>2.0</version>
    <scope>provided</scope>
</dependency>

5) Добавил war.

![JMS-Application-Deployment](http://i0.wp.com/blog.jelastic.com/wp-content/uploads/2013/08/JMS-Application-Deployment.gif)

6) Перешел по ссылки http://localhost:8080/send-message/TestServlet

![JMS-Application](http://i0.wp.com/blog.jelastic.com/wp-content/uploads/2013/08/JMS-Application.gif)
