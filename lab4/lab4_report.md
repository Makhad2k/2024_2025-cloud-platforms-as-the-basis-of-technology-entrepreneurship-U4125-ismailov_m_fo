Решение представлено на доске в MIRO: https://miro.com/app/board/uXjVIUpJbE0=/?share_link_id=165006352426

В рамках лабораторной работы рассматривается пример приложения с тремя стадиями жизненного цикла:

1) Начальная разработка

2) Тестирование партнерами

3) Продовое (production) решение

Для каждой стадии будет:
- Представлена схема архитектуры
- Рассчитана приблизительная стоимость эксплуатации
- Обоснован выбор сервисов Google Cloud Platform

***1. Начальная разработка***

**Описание архитектуры:**
- Пользователь инициирует запуск модели
- Контейнер разворачивается на Cloud Run
- Данные сохраняются в Cloud Storage
- Дополнительная информация — в Firestore (NoSQL БД)

<img width="1477" alt="image" src="https://github.com/user-attachments/assets/a6c14a3f-b740-4aa4-93cc-3428dbe73871" />


**Примерная стоимость:**

![telegram-cloud-photo-size-2-5215546472102228998-y](https://github.com/user-attachments/assets/cbd6e834-19ce-4f89-98b3-66c995b09a4c)


**Обоснование:**
Cloud Run удобен для старта: масштабирование по требованию, нет затрат при простое

Firestore легко интегрируется и не требует ручного управления

Cloud Storage используется для хранения бинарных или медиафайлов

Минимальная инфраструктура — для быстрого прототипа и первых пользователей

<img width="687" alt="image" src="https://github.com/user-attachments/assets/eedcc91c-7c97-4de6-b9cd-de7a7f1ed7fd" />


***2. Тестирование партнерами***

Описание архитектуры:
Перед Cloud Run используется Cloud Load Balancing — для распределения нагрузки

Cloud Run обрабатывает запросы и сохраняет данные

Подключен Cloud Monitoring для отслеживания ошибок

Данные по-прежнему сохраняются в Cloud Storage и Firestore

<img width="1556" alt="image" src="https://github.com/user-attachments/assets/e17ff4e7-ab77-429b-bc3a-22b9fa91a1f2" />


**Примерная стоимость:**

![telegram-cloud-photo-size-2-5215546472102229003-y](https://github.com/user-attachments/assets/05d70b8d-01ac-4beb-bd1b-e0c94fb7bffc)

**Обоснование:**
Cloud Load Balancing позволяет распределить нагрузку между инстансами 

Cloud Monitoring необходим для анализа работы модели под нагрузкой

<img width="573" alt="image" src="https://github.com/user-attachments/assets/b4874d9b-4a42-401f-a6db-c8f8be54f5f4" />

***3. Продовое решение***

**Описание архитектуры:**
- Запросы идут через Cloud Load Balancing
- Контейнеры модели размещаются в Google Kubernetes Engine (GKE)
- Данные сохраняются в Cloud Storage и Cloud SQL
- Используются Cloud Monitoring и Cloud Logging для отслеживания логов и метрик7

![image](https://github.com/user-attachments/assets/37c4fa86-0db1-4577-a3a0-3035c7f8a6f6)


**Примерная стоимость:**

![telegram-cloud-photo-size-2-5215546472102229013-y](https://github.com/user-attachments/assets/bb0248da-47ee-44c8-a265-e9facfe82b05)


**Обоснование:**
GKE обеспечивает стабильную масштабируемость и высокую отказоустойчивость

Cloud SQL (или Firestore) — надежные решения для хранения метаданных и результатов

Cloud Logging и Monitoring — обязательны для анализа, SLA и безопасности

<img width="478" alt="image" src="https://github.com/user-attachments/assets/5c843c87-5edc-4743-a381-eecfe1067c09" />
