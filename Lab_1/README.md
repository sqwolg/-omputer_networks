# Лабораторная работа №1

## Ход работы

### Часть 1. Поднимаем Postgres

#### Запуск docker-compose.yml
<img width="2523" height="624" alt="Снимок экрана 2025-10-19 в 19 02 17" src="https://github.com/user-attachments/assets/c2a63908-133e-4498-8f76-60edbc40f7e0" />
<img width="902" height="302" alt="Снимок экрана 2025-10-19 в 19 04 08" src="https://github.com/user-attachments/assets/c39fd273-16b3-4ee0-a617-1fa2e2798335" />
<img width="1897" height="873" alt="Снимок экрана 2025-10-19 в 19 02 45" src="https://github.com/user-attachments/assets/52892ccc-67e1-4d82-a38e-8fc755499c8d" />
<img width="1127" height="246" alt="Снимок экрана 2025-10-19 в 19 22 43" src="https://github.com/user-attachments/assets/84bbd1ab-f269-4936-96d6-ac676d25f51f" />


### Часть 2. Проверяем репликацию

#### Подключаемся к postgres нодам
<img width="1439" height="669" alt="Снимок экрана 2025-10-19 в 19 01 23" src="https://github.com/user-attachments/assets/147ce06f-11ec-4af6-be8a-c316fbbc8db2" />

#### Создаём таблицу и записываем в неё данные (pg-master)
<img width="1045" height="602" alt="Снимок экрана 2025-10-19 в 18 59 39" src="https://github.com/user-attachments/assets/72b93a91-470d-42bc-960a-36436add5647" />
<img width="1045" height="602" alt="Снимок экрана 2025-10-19 в 18 59 50" src="https://github.com/user-attachments/assets/bb5d7f54-34bd-4a6c-824b-69b8aafdbd42" />

#### Проверка данный и внесение изменений на второй ноде (pg-slave)
<img width="1045" height="602" alt="Снимок экрана 2025-10-19 в 19 00 02" src="https://github.com/user-attachments/assets/4b062dfc-a6cb-4f8c-8bec-0391fef83608" />
<img width="1045" height="602" alt="Снимок экрана 2025-10-19 в 19 00 27" src="https://github.com/user-attachments/assets/24632a79-063f-48b9-8982-660a9a99179b" />

### Часть 3. Делаем высокую доступность

#### Добавляем haproxy
<img width="2609" height="679" alt="Снимок экрана 2025-10-19 в 19 20 41" src="https://github.com/user-attachments/assets/413e7c37-41d0-4331-89a7-1a353cdafaec" />
<img width="2609" height="679" alt="Снимок экрана 2025-10-19 в 19 21 19" src="https://github.com/user-attachments/assets/87872ad3-c68b-43d4-bb71-3ef4d4ea5efe" />
<img width="2609" height="679" alt="Снимок экрана 2025-10-19 в 19 21 12" src="https://github.com/user-attachments/assets/ed46ceb6-8269-41c1-8c1a-a7167e36c654" />
<img width="2447" height="169" alt="Снимок экрана 2025-10-19 в 19 24 09" src="https://github.com/user-attachments/assets/04ff3677-f38c-49ee-aa2b-4a598e6a53f7" />
<img width="1039" height="550" alt="Снимок экрана 2025-10-19 в 19 29 06" src="https://github.com/user-attachments/assets/45145d6c-3801-4cef-aaaf-6fa8fd837adb" />

#### Задание (выключение master-ноды)
<img width="822" height="61" alt="Снимок экрана 2025-10-19 в 19 28 10" src="https://github.com/user-attachments/assets/921f6eae-948e-4daa-ae7b-22259c8cfd30" />
<img width="2610" height="638" alt="Снимок экрана 2025-10-19 в 19 28 03" src="https://github.com/user-attachments/assets/6cc89127-1d09-46e5-8cf1-986d7c378fc5" />

## Ответы на вопросы
> Порты 8008 и 5432 вынесены в разные директивы, expose и ports. По сути, если записать 8008 в ports, то он тоже станет exposed. В чем разница?

- **Expose** – открывает порт только внутри Docker-сети, порт можно использовать только для межконтейнерного взаимодейсвтия.
- **Ports** – пробрасывает порт на хост-машину, тем самым появляется возможность доступа извне. Например, по публчиному адресу хост-машины.

> При обычном перезапуске композ-проекта, будет ли сбилден заново образ? А если предварительно отредактировать файлы postgresX.yml? А если содержимое самого Dockerfile? Почему?

- При обычном перезапуске образ не будет пересобран, только перезапустятся существующие контейнеры.
- При редактировании `postgresX.yml`, образ также не будет пересобран, так как файлы передаются в контейнер как внешние файлы (через `COPY`)
- При редактировании `Dockerfile` также автоматически не будет произведена пересбокра, так как docker-compose по умолчанию использует существующие образы.
- Для запуска с пересборкой образов необходимо использовать команду `docker-compose up --build`
