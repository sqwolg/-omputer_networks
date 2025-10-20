# Лабораторная работа №2

## Ход работы

### Часть 1. Логирование

#### Запуск docker-compose.yml
<img width="2591" height="813" alt="Снимок экрана 2025-10-20 в 21 04 39" src="https://github.com/user-attachments/assets/cb33fcbb-285f-4b20-95c0-5d263c7a3b8f" />

#### Инициализируем Nextcloud
<img width="1243" height="991" alt="Снимок экрана 2025-10-20 в 21 05 39" src="https://github.com/user-attachments/assets/5718ca19-d8cf-434f-aa0b-7201b9bfa21e" />
<img width="2571" height="427" alt="Снимок экрана 2025-10-20 в 21 06 48" src="https://github.com/user-attachments/assets/39db96c1-6f45-43b9-b8ca-fe8275be8583" />
<img width="1232" height="400" alt="Снимок экрана 2025-10-20 в 23 01 58" src="https://github.com/user-attachments/assets/71afe14e-618c-4fb8-8b6c-06d2247b108d" />

### Часть 2. Мониторинг

#### Настраиваем Zabbix
<img width="2571" height="427" alt="Снимок экрана 2025-10-20 в 21 12 04" src="https://github.com/user-attachments/assets/c2df7c1f-7f79-4196-8073-bbaadce3abec" />
<img width="1093" height="104" alt="Снимок экрана 2025-10-20 в 21 13 43" src="https://github.com/user-attachments/assets/bf1b5ccb-9d33-4904-8e50-10f7418ad9b8" />
<img width="2292" height="757" alt="Снимок экрана 2025-10-20 в 21 15 08" src="https://github.com/user-attachments/assets/5eeee058-b595-4112-93c4-a0bce9b707d6" />
<img width="3415" height="757" alt="Снимок экрана 2025-10-20 в 21 16 10" src="https://github.com/user-attachments/assets/edafc570-ace2-47dc-bf67-eb52eb1ea5f9" />

### Часть 3. Визуализация (Grafana)

#### Устанавливаем плагины
<img width="1402" height="182" alt="Снимок экрана 2025-10-20 в 21 17 43" src="https://github.com/user-attachments/assets/a7fc2140-987b-4f11-9f39-8b173b848996" />

#### Настраиваем Loki (data source)
<img width="1803" height="856" alt="Снимок экрана 2025-10-20 в 21 20 20" src="https://github.com/user-attachments/assets/133b5f20-d7b1-41f4-9929-b7256fe2e364" />
<img width="1095" height="278" alt="Снимок экрана 2025-10-20 в 21 20 48" src="https://github.com/user-attachments/assets/93cbac77-0000-4623-82b7-f9356ff83508" />

#### Настраиваем Zabbix (data source)
<img width="1438" height="396" alt="Снимок экрана 2025-10-20 в 21 25 21" src="https://github.com/user-attachments/assets/e5d5bc28-5ebe-4cc6-970d-e1ce646cb613" />

#### Отображение данных
<img width="1673" height="1068" alt="Снимок экрана 2025-10-20 в 21 26 46" src="https://github.com/user-attachments/assets/1a84108f-560d-4589-a099-cb9656136098" />
<img width="1679" height="1064" alt="Снимок экрана 2025-10-20 в 21 27 02" src="https://github.com/user-attachments/assets/9bd835eb-0286-4610-8fc1-d7d97e078f0a" />
<img width="1717" height="1073" alt="Снимок экрана 2025-10-20 в 21 27 39" src="https://github.com/user-attachments/assets/974ad584-3af6-4684-af2d-3f45601a8cb7" />

#### Создание dashboards
<img width="1714" height="1042" alt="Снимок экрана 2025-10-20 в 21 41 49" src="https://github.com/user-attachments/assets/f03c671e-bc63-4b1e-9119-c508670ee304" />
<img width="1708" height="998" alt="Снимок экрана 2025-10-20 в 21 44 19" src="https://github.com/user-attachments/assets/c8f82178-8bd7-4291-80d4-15fc6f0faaf9" />

## Ответы на вопросы
> Чем SLO отличается от SLA?

- SLA (Service Level Agreement) – юридическое соглашение между поставщиком услуг и клиентом, которое определяет условия предоставления услуги. Например, минимальный допустимый уровень доступности сервиса 99,9% времени». При нарушени договорённостей вводятся санкции, прописанные в договоре, например, возврат части средст.
- SLO (Service Level Objective) - это целевые значения метрик, которые используются для внутреннего контроля работоспособности сервисов и услуг. Например, цель, к которой стремится команда разработки.

> Чем отличается инкрементальный бэкап от дифференциального?

- Дифференциальный бэкап – копируются все данные, измененные с момента последнего полного бэкапа. Для восстановления потребуется полный бэкап и последний дифференциальный.
- Инкрементальный бэкап – копируются все данные, измененные с момента любого последнего бэкапа. Выигрыает по размеру, но для восстановления потребуется полный бэкап и все инкрементальные бэкапы по порядку.

> В чем разница между мониторингом и observability?

- Мониторинг (реактивный подход) — отслеживание заранее известных метрик.
- Observability (проактивный подход) — это возможность понять поведение системы на основе данных (логов, метрик, трассировок), даже если проблема ранее не была предсказана.


