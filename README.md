## Домашнее задание к занятию «Очереди RabbitMQ»-Рустам Ахмадеев
Инструкция по выполнению домашнего задания
1. Сделайте fork репозитория c шаблоном решения к себе в Github и переименуйте его по названию или номеру занятия, например, https://github.com/имя-вашего-репозитория/gitlab-hw или https://github.com/имя-вашего-репозитория/8-03-hw).
2. Выполните клонирование этого репозитория к себе на ПК с помощью команды git clone.
3. Выполните домашнее задание и заполните у себя локально этот файл README.md:
- впишите вверху название занятия и ваши фамилию и имя;
- в каждом задании добавьте решение в требуемом виде: текст/код/скриншоты/ссылка;
- для корректного добавления скриншотов воспользуйтесь инструкцией «Как вставить скриншот в шаблон с решением»;
- при оформлении используйте возможности языка разметки md. Коротко об этом можно посмотреть в инструкции по MarkDown.
4. После завершения работы над домашним заданием сделайте коммит (git commit -m "comment") и отправьте его на Github (git push origin).
5. Для проверки домашнего задания преподавателем в личном кабинете прикрепите и отправьте ссылку на решение в виде md-файла в вашем Github.
6. Любые вопросы задавайте в чате учебной группы и/или в разделе «Вопросы по заданию» в личном кабинете.
Желаем успехов в выполнении домашнего задания.
---
## Задание 1. Установка RabbitMQ
Используя Vagrant или VirtualBox, создайте виртуальную машину и установите RabbitMQ. Добавьте management plug-in и зайдите в веб-интерфейс.
Итогом выполнения домашнего задания будет приложенный скриншот веб-интерфейса RabbitMQ.

Решение 1

![alt text](https://github.com/ahmrust/RabbitMQ/blob/main/img/1.png)
---
## Задание 2. Отправка и получение сообщений
Используя приложенные скрипты, проведите тестовую отправку и получение сообщения. Для отправки сообщений необходимо запустить скрипт producer.py.
Для работы скриптов вам необходимо установить Python версии 3 и библиотеку Pika. Также в скриптах нужно указать IP-адрес машины, на которой запущен RabbitMQ, заменив localhost на нужный IP.
$ pip install pika
Зайдите в веб-интерфейс, найдите очередь под названием hello и сделайте скриншот. После чего запустите второй скрипт consumer.py и сделайте скриншот результата выполнения скрипта
В качестве решения домашнего задания приложите оба скриншота, сделанных на этапе выполнения.
Для закрепления материала можете попробовать модифицировать скрипты, чтобы поменять название очереди и отправляемое сообщение.

Решение 2

![alt text](https://github.com/ahmrust/RabbitMQ/blob/main/img/2.png)
![alt text](https://github.com/ahmrust/RabbitMQ/blob/main/img/3.png)
---

## Задание 3. Подготовка HA кластера
Используя Vagrant или VirtualBox, создайте вторую виртуальную машину и установите RabbitMQ. Добавьте в файл hosts название и IP-адрес каждой машины, чтобы машины могли видеть друг друга по имени.
Пример содержимого hosts файла:
$ cat /etc/hosts
192.168.0.10 rmq01
192.168.0.11 rmq02
После этого ваши машины могут пинговаться по имени.
Затем объедините две машины в кластер и создайте политику ha-all на все очереди.
В качестве решения домашнего задания приложите скриншоты из веб-интерфейса с информацией о доступных нодах в кластере и включённой политикой.
Также приложите вывод команды с двух нод:
$ rabbitmqctl cluster_status
Для закрепления материала снова запустите скрипт producer.py и приложите скриншот выполнения команды на каждой из нод:
$ rabbitmqadmin get queue='hello'
После чего попробуйте отключить одну из нод, желательно ту, к которой подключались из скрипта, затем поправьте параметры подключения в скрипте consumer.py на вторую ноду и запустите его.
Приложите скриншот результата работы второго скрипта.

Решение 3

![alt text](https://github.com/ahmrust/RabbitMQ/blob/main/img/4.png)
![alt text](https://github.com/ahmrust/RabbitMQ/blob/main/img/5.png)
![alt text](https://github.com/ahmrust/RabbitMQ/blob/main/img/6.png)
![alt text](https://github.com/ahmrust/RabbitMQ/blob/main/img/7.png)
![alt text](https://github.com/ahmrust/RabbitMQ/blob/main/img/8.png)
![alt text](https://github.com/ahmrust/RabbitMQ/blob/main/img/9.png)
![alt text](https://github.com/ahmrust/RabbitMQ/blob/main/img/10.png)
---
Дополнительные задания (со звёздочкой*)

## Эти задания дополнительные, то есть не обязательные к выполнению, и никак не повлияют на получение вами зачёта по этому домашнему заданию. Вы можете их выполнить, если хотите глубже шире разобраться в материале.
* Задание 4. Ansible playbook
Напишите плейбук, который будет производить установку RabbitMQ на любое количество нод и объединять их в кластер. При этом будет автоматически создавать политику ha-all.
Готовый плейбук разместите в своём репозитории.
