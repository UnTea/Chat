# Чат

Сделать приложение веб-чата. Пользователи заходят на страницу, где есть форма ввода сообщения (html input) и кнопка 
Отправить. Под ними - список сообщений обычным текстом (каждое сообщение обрамляется в отдельный `<p></p>`
  
Приложение запустить в `docker-compose`. Использовать следующие сервисы:
* Nginx в качестве реверс-прокси (входящий узел) и балансировщика
* Backend на Golang или Python
* NATS
  
Необходимо запустить несколько копий (реплик) Backend. Между ними настроить балансировку round-robin. 
  
NATS использовать в качестве брокера сообщений.
  
Для связи между Backend и Front использовать Websockets.
    
Заходящий в чат пользователь НЕ видит истории, то есть тех сообщений, которые были отправлены до его подключения.

# Чат 2.0

Продолжение предыдущего задания.
  
Надо сделать раздельные чаты. Пользователь, заходящий на основную страницу (`http://.../index.html`) автоматически 
создает новую чат-комнату и автоматически переходит в нее. Чат-комната выглядит как `http://.../some_id`
  
Все пользователи, заходящие сразу по этому URL (в эту чат-комнату), видят историю и общаются друг с другом. Если 
пользователь пытается зайти в несуществующую чат-комнату, он получает 404.
  
В качестве БД использовать Redis или Mongo.