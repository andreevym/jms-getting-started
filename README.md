# jms-getting-started
This section describes the sending and receiving message. Getting started with the GlassFish application server.


1) Установил glassfish.
https://glassfish.java.net/download.html

2) Распаковал и запустил
asadmin start-domain

из-за баги в UI добавил очередь через консоль:
http://stackoverflow.com/questions/33731097/cannot-create-any-jms-resource-through-glassfish-4-1-web-admin

3) Зашел в панель управление через cmd
asadmin

4) Добавил фабрику.
asadmin> create-jms-resource --host localhost --port 4848 --restype javax.jms.QueueConnectionFactory --property  Name=MyQCF jms/QCF1


Встроенное изображение 1

5) Добавил очередь.
create-jms-resource --host localhost --port 4848 --restype javax.jms.Queue --property Name=PhysicalQueue jms/myQueue

6) Доработал проект:
изменил зависимость, на:
<dependency>
    <groupId>javax.jms</groupId>
    <artifactId>javax.jms-api</artifactId>
    <version>2.0</version>
    <scope>provided</scope>
</dependency>

7) Добавил war.
Встроенное изображение 3


8) Перешел по ссылки http://localhost:8080/send-message/TestServlet

-- Воспользовался статьей:
https://dzone.com/articles/jms-application-deployment
