# 10.2_Grafana_Aleksandr_Molokov

### Задание 1

1. Используя директорию [help](./help) внутри этого домашнего задания, запустите связку prometheus-grafana.
2. Зайдите в веб-интерфейс grafana, используя авторизационные данные, указанные в манифесте docker-compose.
3. Подключите поднятый вами prometheus, как источник данных.
4. Решение домашнего задания — скриншот веб-интерфейса grafana со списком подключенных Datasource.

# Ответ

1. Развертывание на ВМ в YandexCloud
![1 create VM](https://user-images.githubusercontent.com/109212419/228349839-045ebe9f-b6eb-4e38-b498-6815d9f8fa1a.jpg)

![1 deploy docker into VM](https://user-images.githubusercontent.com/109212419/228349869-d81f9400-dd06-42ca-862e-75c6fe971e0d.jpg)

2. Зайдите в веб-интерфейс grafana, используя авторизационные данные, указанные в манифесте docker-compose.

![1-2 Grafana](https://user-images.githubusercontent.com/109212419/228350110-3ac52291-d540-4a6a-a5e9-5c61c566b545.jpg)

3.Подключите поднятый вами prometheus, как источник данных.

![1-3 add prometheus](https://user-images.githubusercontent.com/109212419/228359899-833d14ff-1d05-4c1f-97a9-296f281ff7d9.jpg)

4.Решение домашнего задания — скриншот веб-интерфейса grafana со списком подключенных Datasource.

![1-3 add prometheus -1](https://user-images.githubusercontent.com/109212419/228359974-db4c2e82-6f03-4fb9-b7ad-65de03cfb605.jpg)


## Задание 2

Изучите самостоятельно ресурсы:

1. [PromQL tutorial for beginners and humans](https://valyala.medium.com/promql-tutorial-for-beginners-9ab455142085).
1. [Understanding Machine CPU usage](https://www.robustperception.io/understanding-machine-cpu-usage).
1. [Introduction to PromQL, the Prometheus query language](https://grafana.com/blog/2020/02/04/introduction-to-promql-the-prometheus-query-language/).

Создайте Dashboard и в ней создайте Panels:

- утилизация CPU для nodeexporter (в процентах, 100-idle);
- CPULA 1/5/15;
- количество свободной оперативной памяти;
- количество места на файловой системе.

Для решения этого задания приведите promql-запросы для выдачи этих метрик, а также скриншот получившейся Dashboard.

# Ответ



promql-запросы

- утилизация CPU для nodeexporter (в процентах, 100-idle);
rate(node_cpu_seconds_total[5m])

- CPULA 1/5/15;
node_load1{instance="nodeexporter:9100", job="nodeexporter"}
node_load5{instance="nodeexporter:9100", job="nodeexporter"}
node_load15{instance="nodeexporter:9100", job="nodeexporter"}

- количество свободной оперативной памяти;
node_memory_MemFree_bytes{instance="nodeexporter:9100", job="nodeexporter"}

- количество места на файловой системе.
node_filesystem_free_bytes{device="/dev/vda2", fstype="ext4", instance="nodeexporter:9100", job="nodeexporter", mountpoint="/"}

## Задание 3

1. Создайте для каждой Dashboard подходящее правило alert — можно обратиться к первой лекции в блоке «Мониторинг».
1. В качестве решения задания приведите скриншот вашей итоговой Dashboard.

# Ответ

![3 allert](https://user-images.githubusercontent.com/109212419/228965252-79b065d7-7902-4488-b39e-7d73a7adc224.jpg)


## Задание 4

1. Сохраните ваш Dashboard.Для этого перейдите в настройки Dashboard, выберите в боковом меню «JSON MODEL». Далее скопируйте отображаемое json-содержимое в отдельный файл и сохраните его.
1. В качестве решения задания приведите листинг этого файла.

# Ответ

![Dashboard.json](https://github.com/ALEMOLOKOV/10.2_Grafana_Aleksandr_Molokov/blob/115181ddf354977993f3eac7a70ef5a2efc3b2cd/dashboard.json)
