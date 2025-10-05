# Домашнее задание к занятию "`Кластеризация и балансировка нагрузки`" - `Фомичев Анатолий`



### Задание 1

`Приведите ответ в свободной форме........`

1. [haproxy.cfg](https://github.com/SLzDevOps/Netology_cluster-balance2/blob/main/haproxy1.cfg)
2. `Заполните здесь этапы выполнения, если требуется ....`


`
![alt text](https://github.com/SLzDevOps/Netology_cluster-balance2/blob/main/Screenshot_558.png).
![alt text](https://github.com/SLzDevOps/Netology_cluster-balance2/blob/main/Screenshot_559.png).
![alt text](https://github.com/SLzDevOps/Netology_cluster-balance2/blob/main/Screenshot_560.png).
![alt text](https://github.com/SLzDevOps/Netology_cluster-balance2/blob/main/Screenshot_561.png).
![alt text](https://github.com/SLzDevOps/Netology_cluster-balance2/blob/main/Screenshot_562.png).
![alt text](https://github.com/SLzDevOps/Netology_cluster-balance2/blob/main/Screenshot_563.png).
![alt text](https://github.com/SLzDevOps/Netology_cluster-balance2/blob/main/Screenshot_565.png).
![alt text](https://github.com/SLzDevOps/Netology_cluster-balance2/blob/main/Screenshot_567.png).


---

### Задание 2

`Приведите ответ в свободной форме........`

1. [haproxy.cfg](https://github.com/SLzDevOps/Netology_cluster-balance2/blob/main/haproxy2.cfg)
2. `Заполните здесь этапы выполнения, если требуется ....`


`
![alt text](https://github.com/SLzDevOps/Netology_cluster-balance2/blob/main/Screenshot_569.png).
![alt text](https://github.com/SLzDevOps/Netology_cluster-balance2/blob/main/Screenshot_568.png).

### Доработка

`Просто обращение к example.local, который нигде не указан`

![alt text](https://github.com/SLzDevOps/Netology_cluster-balance2/blob/main/Screenshot_572.png).

`Внесены правки в haproxy.cfg, выполнен релод и запросы`

![alt text](https://github.com/SLzDevOps/Netology_cluster-balance2/blob/main/Screenshot_574.png).
![alt text](https://github.com/SLzDevOps/Netology_cluster-balance2/blob/main/Screenshot_576.png).


`так я и не понял откуда он взялся, example.local, в видео везде .сом, тут поправить 2 строчки и .local сделать....
Если не прав, объясните пожалуйста!! `


### Доработка 2


При запросе с использованием домена example.local ( curl -H 'Host:example.local' http://127.0.0.1:8088 ) - все работает, идет балансировка, так как example.local указан в ACL haproxy.cfg, и обращение к бэкенду идет через него:
        acl ACL_example.local hdr(host) -i example.local
        use_backend web_servers if ACL_example.local

![alt text](https://github.com/SLzDevOps/Netology_cluster-balance2/blob/main/Screenshot_577.png).


Если отправить запрос к HAProxy без указания заголовка Host: example.local, то согласно текущей конфигурации, этот запрос не попадёт в backend. Запрос будет обработан frontend-ом, а на фронтэнде т отсутствует условие для обработки запросов. Так как в haproxy.cfg нет указания другого backend-а, настроенного для обработки запросов без указанного условия - запросы, отправляемые без заголовка example.local, останутся необработанными - 503 (Service Unavailable).


![alt text](https://github.com/SLzDevOps/Netology_cluster-balance2/blob/main/Screenshot_578.png).



## Спасибо!




